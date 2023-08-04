# WebScraping_Project

This project involves scraping data from the 2023 Fortune Global 500 list to extract the financial details of 14 Canadian companies for fiscal year 2022. The data encompasses revenue, net profit, employee count, industry sector, and headquarters. Utilizing Python's BeautifulSoup and requests, the web scraping process retrieves this information. Subsequently, data is cleaned, transformed, and analyzed, employing libraries like Matplotlib. The project aims to provide insights into the performance and industry representation of Canadian businesses on a global scale, offering valuable information for business analysis and decision-making.

**#CODE**   

from bs4 import BeautifulSoup
import requests
In [24]:
url = 'https://en.wikipedia.org/wiki/List_of_largest_companies_in_Canada'
page = requests.get(url)
soup = BeautifulSoup(page.text,'html')
In [25]:
print(soup)
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 2/48
<!DOCTYPE html>
<html class="client-nojs vector-feature-language-in-header-enabled vector-feature-lan
guage-in-main-page-header-disabled vector-feature-sticky-header-disabled vector-featu
re-page-tools-pinned-disabled vector-feature-toc-pinned-enabled vector-feature-main-m
enu-pinned-disabled vector-feature-limited-width-enabled vector-feature-limited-width
-content-enabled vector-feature-zebra-design-disabled" dir="ltr" lang="en">
<head>
<meta charset="utf-8"/>
<title>List of largest companies in Canada - Wikipedia</title>
<script>document.documentElement.className="client-js vector-feature-language-in-head
er-enabled vector-feature-language-in-main-page-header-disabled vector-feature-sticky
-header-disabled vector-feature-page-tools-pinned-disabled vector-feature-toc-pinnedenabled vector-feature-main-menu-pinned-disabled vector-feature-limited-width-enabled
vector-feature-limited-width-content-enabled vector-feature-zebra-design-disabled";(f
unction(){var cookie=document.cookie.match(/(?:^|; )enwikimwclientprefs=([^;]+)/);if
(cookie){var featureName=cookie[1];document.documentElement.className=document.docume
ntElement.className.replace(featureName+'-enabled',featureName+'-disabled');}}());RLC
ONF={"wgBreakFrames":false,"wgSeparatorTransformTable":["",""],"wgDigitTransformTabl
e":["",""],"wgDefaultDateFormat":"dmy","wgMonthNames":["","January","February","Marc
h","April","May","June","July","August","September","October","November","Decembe
r"],"wgRequestId":"e6bc0476-9737-47b7-9c38-6c2dd268c4ec","wgCSPNonce":false,
"wgCanonicalNamespace":"","wgCanonicalSpecialPageName":false,"wgNamespaceNumber":0,"w
gPageName":"List_of_largest_companies_in_Canada","wgTitle":"List of largest companies
in Canada","wgCurRevisionId":1168712460,"wgRevisionId":1168712460,"wgArticleId":61383
406,"wgIsArticle":true,"wgIsRedirect":false,"wgAction":"view","wgUserName":null,"wgUs
erGroups":["*"],"wgCategories":["Articles with short description","Short description
is different from Wikidata","Lists of largest private companies by country","Lists of
companies of Canada","Economy of Canada"],"wgPageViewLanguage":"en","wgPageContentLan
guage":"en","wgPageContentModel":"wikitext","wgRelevantPageName":"List_of_largest_com
panies_in_Canada","wgRelevantArticleId":61383406,"wgIsProbablyEditable":true,"wgRelev
antPageIsProbablyEditable":true,"wgRestrictionEdit":[],"wgRestrictionMove":[],"wgFlag
gedRevsParams":{"tags":{"status":{"levels":1}}},"wgVisualEditor":{"pageLanguageCod
e":"en","pageLanguageDir":"ltr","pageVariantFallbacks":"en"},
"wgMFDisplayWikibaseDescriptions":{"search":true,"watchlist":true,"tagline":false,"ne
arby":true},"wgWMESchemaEditAttemptStepOversample":false,"wgWMEPageLength":10000,"wgN
oticeProject":"wikipedia","wgMediaViewerOnClick":true,"wgMediaViewerEnabledByDefaul
t":true,"wgPopupsFlags":10,"wgULSCurrentAutonym":"English","wgEditSubmitButtonLabelPu
blish":true,"wgCentralAuthMobileDomain":false,"wgULSPosition":"interlanguage","wgULSi
sCompactLinksEnabled":true,"wgULSisLanguageSelectorEmpty":false,"wgWikibaseItemId":"Q
1371361","GEHomepageSuggestedEditsEnableTopics":true,"wgGETopicsMatchModeEnabled":fal
se,"wgGEStructuredTaskRejectionReasonTextInputEnabled":false,"wgGELevelingUpEnabledFo
rUser":false};RLSTATE={"skins.vector.user.styles":"ready","ext.globalCssJs.user.style
s":"ready","site.styles":"ready","user.styles":"ready","skins.vector.user":"ready","e
xt.globalCssJs.user":"ready","user":"ready","user.options":"loading","ext.cite.style
s":"ready","codex-search-styles":"ready","skins.vector.styles":
"ready","skins.vector.icons":"ready","jquery.tablesorter.styles":"ready","ext.visualE
ditor.desktopArticleTarget.noscript":"ready","ext.wikimediaBadges":"ready","ext.uls.i
nterlanguage":"ready","wikibase.client.init":"ready"};RLPAGEMODULES=["ext.cite.ux-enh
ancements","site","mediawiki.page.ready","jquery.tablesorter","mediawiki.toc","skins.
vector.js","ext.visualEditor.desktopArticleTarget.init","ext.visualEditor.targetLoade
r","ext.eventLogging","ext.wikimediaEvents","ext.navigationTiming","ext.cx.eventloggi
ng.campaigns","ext.quicksurveys.init","ext.centralNotice.geoIP","ext.centralNotice.st
artUp","ext.gadget.ReferenceTooltips","ext.gadget.charinsert","ext.gadget.extra-toolb
ar-buttons","ext.gadget.switcher","ext.centralauth.centralautologin","ext.popups","ex
t.echo.centralauth","ext.uls.compactlinks","ext.uls.interface","ext.cx.uls.quick.acti
ons","wikibase.client.vector-2022","ext.growthExperiments.SuggestedEditSession"];</sc
ript>
<script>(RLQ=window.RLQ||[]).push(function(){mw.loader.implement("user.options@12s5
i",function($,jQuery,require,module){mw.user.tokens.set({"patrolToken":"+\\","watchTo
ken":"+\\","csrfToken":"+\\"});});});</script>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 3/48
<link href="/w/load.php?lang=en&amp;modules=codex-search-styles%7Cext.cite.styles%7Ce
xt.uls.interlanguage%7Cext.visualEditor.desktopArticleTarget.noscript%7Cext.wikimedia
Badges%7Cjquery.tablesorter.styles%7Cskins.vector.icons%2Cstyles%7Cwikibase.client.in
it&amp;only=styles&amp;skin=vector-2022" rel="stylesheet"/>
<script async="" src="/w/load.php?lang=en&amp;modules=startup&amp;only=scripts&amp;ra
w=1&amp;skin=vector-2022"></script>
<meta content="" name="ResourceLoaderDynamicStyles"/>
<link href="/w/load.php?lang=en&amp;modules=site.styles&amp;only=styles&amp;skin=vect
or-2022" rel="stylesheet"/>
<meta content="MediaWiki 1.41.0-wmf.20" name="generator"/>
<meta content="origin" name="referrer"/>
<meta content="origin-when-crossorigin" name="referrer"/>
<meta content="origin-when-cross-origin" name="referrer"/>
<meta content="max-image-preview:standard" name="robots"/>
<meta content="telephone=no" name="format-detection"/>
<meta content="width=1000" name="viewport"/>
<meta content="List of largest companies in Canada - Wikipedia" property="og:title"/>
<meta content="website" property="og:type"/>
<link href="//en.m.wikipedia.org/wiki/List_of_largest_companies_in_Canada" media="onl
y screen and (max-width: 720px)" rel="alternate"/>
<link href="/w/index.php?title=List_of_largest_companies_in_Canada&amp;action=edit" r
el="alternate" title="Edit this page" type="application/x-wiki"/>
<link href="/static/apple-touch/wikipedia.png" rel="apple-touch-icon"/>
<link href="/static/favicon/wikipedia.ico" rel="icon"/>
<link href="/w/opensearch_desc.php" rel="search" title="Wikipedia (en)" type="applica
tion/opensearchdescription+xml"/>
<link href="//en.wikipedia.org/w/api.php?action=rsd" rel="EditURI" type="application/
rsd+xml"/>
<link href="https://en.wikipedia.org/wiki/List_of_largest_companies_in_Canada" rel="c
anonical"/>
<link href="https://creativecommons.org/licenses/by-sa/4.0/deed.en" rel="license"/>
<link href="/w/index.php?title=Special:RecentChanges&amp;feed=atom" rel="alternate" t
itle="Wikipedia Atom feed" type="application/atom+xml"/>
<link href="//meta.wikimedia.org" rel="dns-prefetch"/>
<link href="//login.wikimedia.org" rel="dns-prefetch"/>
</head>
<body class="skin-vector skin-vector-search-vue mediawiki ltr sitedir-ltr mw-hide-emp
ty-elt ns-0 ns-subject mw-editable page-List_of_largest_companies_in_Canada rootpageList_of_largest_companies_in_Canada skin-vector-2022 action-view"><a class="mw-jump-l
ink" href="#bodyContent">Jump to content</a>
<div class="vector-header-container">
<header class="vector-header mw-header">
<div class="vector-header-start">
<nav aria-label="Site" class="vector-main-menu-landmark" role="navigation">
<div class="vector-dropdown vector-main-menu-dropdown vector-button-flush-left vector
-button-flush-right" id="vector-main-menu-dropdown">
<input aria-haspopup="true" aria-label="Main menu" class="vector-dropdown-checkbox" d
ata-event-name="ui.dropdown-vector-main-menu-dropdown" id="vector-main-menu-dropdowncheckbox" role="button" type="checkbox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet cdx-button--icon-only"
for="vector-main-menu-dropdown-checkbox" id="vector-main-menu-dropdown-label"><span c
lass="vector-icon mw-ui-icon-menu mw-ui-icon-wikimedia-menu"></span>
<span class="vector-dropdown-label-text">Main menu</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-unpinned-container" id="vector-main-menu-unpinned-container">
<div class="vector-main-menu vector-pinnable-element" id="vector-main-menu">
<div class="vector-pinnable-header vector-main-menu-pinnable-header vector-pinnable-h
eader-unpinned" data-feature-name="main-menu-pinned" data-pinnable-element-id="vector
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 4/48
-main-menu" data-pinned-container-id="vector-main-menu-pinned-container" data-unpinne
d-container-id="vector-main-menu-unpinned-container">
<div class="vector-pinnable-header-label">Main menu</div>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-pin-butto
n" data-event-name="pinnable-header.vector-main-menu.pin">move to sidebar</button>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-unpin-butt
on" data-event-name="pinnable-header.vector-main-menu.unpin">hide</button>
</div>
<div class="vector-menu mw-portlet mw-portlet-navigation" id="p-navigation">
<div class="vector-menu-heading">
Navigation
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="mw-list-item" id="n-mainpage-description"><a accesskey="z" href="/wiki/Mai
n_Page" title="Visit the main page [z]"><span>Main page</span></a></li><li class="mwlist-item" id="n-contents"><a href="/wiki/Wikipedia:Contents" title="Guides to browsi
ng Wikipedia"><span>Contents</span></a></li><li class="mw-list-item" id="n-currenteve
nts"><a href="/wiki/Portal:Current_events" title="Articles related to current event
s"><span>Current events</span></a></li><li class="mw-list-item" id="n-randompage"><a
accesskey="x" href="/wiki/Special:Random" title="Visit a randomly selected article
[x]"><span>Random article</span></a></li><li class="mw-list-item" id="n-aboutsite"><a
href="/wiki/Wikipedia:About" title="Learn about Wikipedia and how it works"><span>Abo
ut Wikipedia</span></a></li><li class="mw-list-item" id="n-contactpage"><a href="//e
n.wikipedia.org/wiki/Wikipedia:Contact_us" title="How to contact Wikipedia"><span>Con
tact us</span></a></li><li class="mw-list-item" id="n-sitesupport"><a href="https://d
onate.wikimedia.org/wiki/Special:FundraiserRedirector?utm_source=donate&amp;utm_mediu
m=sidebar&amp;utm_campaign=C13_en.wikipedia.org&amp;uselang=en" title="Support us by
donating to the Wikimedia Foundation"><span>Donate</span></a></li>
</ul>
</div>
</div>
<div class="vector-menu mw-portlet mw-portlet-interaction" id="p-interaction">
<div class="vector-menu-heading">
Contribute
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="mw-list-item" id="n-help"><a href="/wiki/Help:Contents" title="Guidance on
how to use and edit Wikipedia"><span>Help</span></a></li><li class="mw-list-item" id
="n-introduction"><a href="/wiki/Help:Introduction" title="Learn how to edit Wikipedi
a"><span>Learn to edit</span></a></li><li class="mw-list-item" id="n-portal"><a href
="/wiki/Wikipedia:Community_portal" title="The hub for editors"><span>Community porta
l</span></a></li><li class="mw-list-item" id="n-recentchanges"><a accesskey="r" href
="/wiki/Special:RecentChanges" title="A list of recent changes to Wikipedia [r]"><spa
n>Recent changes</span></a></li><li class="mw-list-item" id="n-upload"><a href="/wik
i/Wikipedia:File_upload_wizard" title="Add images or other media for use on Wikipedi
a"><span>Upload file</span></a></li>
</ul>
</div>
</div>
<div class="vector-main-menu-action vector-main-menu-action-lang-alert">
<div class="vector-main-menu-action-item">
<div class="vector-main-menu-action-heading vector-menu-heading">Languages</div>
<div class="vector-main-menu-action-content vector-menu-content">
<div class="mw-message-box cdx-message cdx-message--block mw-message-box-notice cdx-m
essage--notice vector-language-sidebar-alert"><span class="cdx-message__icon"></span>
<div class="cdx-message__content">Language links are at the top of the page across fr
om the title.</div></div>
</div>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 5/48
</div>
</div>
</div>
</div>
</div>
</div>
</nav>
<a class="mw-logo" href="/wiki/Main_Page">
<img alt="" aria-hidden="true" class="mw-logo-icon" height="50" src="/static/images/i
cons/wikipedia.png" width="50"/>
<span class="mw-logo-container">
<img alt="Wikipedia" class="mw-logo-wordmark" src="/static/images/mobile/copyright/wi
kipedia-wordmark-en.svg" style="width: 7.5em; height: 1.125em;"/>
<img alt="The Free Encyclopedia" class="mw-logo-tagline" height="13" src="/static/ima
ges/mobile/copyright/wikipedia-tagline-en.svg" style="width: 7.3125em; height: 0.8125
em;" width="117"/>
</span>
</a>
</div>
<div class="vector-header-end">
<div class="vector-search-box-vue vector-search-box-collapses vector-search-box-showthumbnail vector-search-box-auto-expand-width vector-search-box" id="p-search" role
="search">
<a accesskey="f" class="cdx-button cdx-button--fake-button cdx-button--fake-button--e
nabled cdx-button--weight-quiet cdx-button--icon-only search-toggle" href="/wiki/Spec
ial:Search" id="" title="Search Wikipedia [f]"><span class="vector-icon mw-ui-icon-se
arch mw-ui-icon-wikimedia-search"></span>
<span>Search</span>
</a>
<div class="vector-typeahead-search-container">
<div class="cdx-typeahead-search cdx-typeahead-search--show-thumbnail cdx-typeahead-s
earch--auto-expand-width">
<form action="/w/index.php" class="cdx-search-input cdx-search-input--has-end-button"
id="searchform">
<div class="cdx-search-input__input-wrapper" data-search-loc="header-moved" id="simpl
eSearch">
<div class="cdx-text-input cdx-text-input--has-start-icon">
<input accesskey="f" aria-label="Search Wikipedia" autocapitalize="sentences" class
="cdx-text-input__input" id="searchInput" name="search" placeholder="Search Wikipedi
a" title="Search Wikipedia [f]" type="search"/>
<span class="cdx-text-input__icon cdx-text-input__start-icon"></span>
</div>
<input name="title" type="hidden" value="Special:Search"/>
</div>
<button class="cdx-button cdx-search-input__end-button">Search</button>
</form>
</div>
</div>
</div>
<nav aria-label="Personal tools" class="vector-user-links" role="navigation">
<div class="vector-menu mw-portlet mw-portlet-vector-user-menu-overflow" id="p-vector
-user-menu-overflow">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="user-links-collapsible-item mw-list-item" id="pt-createaccount-2"><a href
="/w/index.php?title=Special:CreateAccount&amp;returnto=List+of+largest+companies+in+
Canada" title="You are encouraged to create an account and log in; however, it is not
mandatory"><span>Create account</span></a></li><li class="user-links-collapsible-item
mw-list-item" id="pt-login-2"><a accesskey="o" href="/w/index.php?title=Special:UserL
ogin&amp;returnto=List+of+largest+companies+in+Canada" title="You're encouraged to lo
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 6/48
g in; however, it's not mandatory. [o]"><span>Log in</span></a></li>
</ul>
</div>
</div>
<div class="vector-dropdown vector-user-menu vector-button-flush-right vector-user-me
nu-logged-out" id="vector-user-links-dropdown" title="Log in and more options">
<input aria-haspopup="true" aria-label="Personal tools" class="vector-dropdown-checkb
ox" data-event-name="ui.dropdown-vector-user-links-dropdown" id="vector-user-links-dr
opdown-checkbox" role="button" type="checkbox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet cdx-button--icon-only"
for="vector-user-links-dropdown-checkbox" id="vector-user-links-dropdown-label"><span
class="vector-icon mw-ui-icon-ellipsis mw-ui-icon-wikimedia-ellipsis"></span>
<span class="vector-dropdown-label-text">Personal tools</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-menu mw-portlet mw-portlet-personal user-links-collapsible-item" i
d="p-personal" title="User menu">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="user-links-collapsible-item mw-list-item" id="pt-createaccount"><a href="/
w/index.php?title=Special:CreateAccount&amp;returnto=List+of+largest+companies+in+Can
ada" title="You are encouraged to create an account and log in; however, it is not ma
ndatory"><span class="vector-icon mw-ui-icon-userAdd mw-ui-icon-wikimedia-userAdd"></
span> <span>Create account</span></a></li><li class="user-links-collapsible-item mw-l
ist-item" id="pt-login"><a accesskey="o" href="/w/index.php?title=Special:UserLogin&a
mp;returnto=List+of+largest+companies+in+Canada" title="You're encouraged to log in;
however, it's not mandatory. [o]"><span class="vector-icon mw-ui-icon-logIn mw-ui-ico
n-wikimedia-logIn"></span> <span>Log in</span></a></li>
</ul>
</div>
</div>
<div class="vector-menu mw-portlet mw-portlet-user-menu-anon-editor" id="p-user-menuanon-editor">
<div class="vector-menu-heading">
Pages for logged out editors <a aria-label="Learn more about editing"
href="/wiki/Help:Introduction"><span>learn more</span></a>
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="mw-list-item" id="pt-anoncontribs"><a accesskey="y" href="/wiki/Special:My
Contributions" title="A list of edits made from this IP address [y]"><span>Contributi
ons</span></a></li><li class="mw-list-item" id="pt-anontalk"><a accesskey="n" href="/
wiki/Special:MyTalk" title="Discussion about edits from this IP address [n]"><span>Ta
lk</span></a></li>
</ul>
</div>
</div>
</div>
</div>
</nav>
</div>
</header>
</div>
<div class="mw-page-container">
<div class="mw-page-container-inner">
<div class="vector-main-menu-container">
<div id="mw-navigation">
<nav aria-label="Site" class="vector-main-menu-landmark" id="mw-panel" role="navigati
on">
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 7/48
<div class="vector-pinned-container" id="vector-main-menu-pinned-container">
</div>
</nav>
</div>
</div>
<div class="vector-sitenotice-container">
<div id="siteNotice"><!-- CentralNotice --></div>
</div>
<input class="vector-menu-checkbox" id="vector-toc-collapsed-checkbox" type="checkbo
x"/>
<nav aria-label="Contents" class="mw-table-of-contents-container vector-toc-landmark
vector-sticky-pinned-container" data-event-name="ui.sidebar-toc" id="mw-panel-toc" ro
le="navigation">
<div class="vector-pinned-container" id="vector-toc-pinned-container">
<div class="vector-toc vector-pinnable-element" id="vector-toc">
<div class="vector-pinnable-header vector-toc-pinnable-header vector-pinnable-headerpinned" data-feature-name="toc-pinned" data-pinnable-element-id="vector-toc">
<h2 class="vector-pinnable-header-label">Contents</h2>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-pin-butto
n" data-event-name="pinnable-header.vector-toc.pin">move to sidebar</button>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-unpin-butt
on" data-event-name="pinnable-header.vector-toc.unpin">hide</button>
</div>
<ul class="vector-toc-contents" id="mw-panel-toc-list">
<li class="vector-toc-list-item vector-toc-level-1" id="toc-mw-content-text">
<a class="vector-toc-link" href="#">
<div class="vector-toc-text">(Top)</div>
</a>
</li>
<li class="vector-toc-list-item vector-toc-level-1 vector-toc-list-item-expanded" id
="toc-2023_Fortune_list">
<a class="vector-toc-link" href="#2023_Fortune_list">
<div class="vector-toc-text">
<span class="vector-toc-numb">1</span>2023 <i>Fortune</i> list</div>
</a>
<ul class="vector-toc-list" id="toc-2023_Fortune_list-sublist">
</ul>
</li>
<li class="vector-toc-list-item vector-toc-level-1 vector-toc-list-item-expanded" id
="toc-2019_Forbes_list">
<a class="vector-toc-link" href="#2019_Forbes_list">
<div class="vector-toc-text">
<span class="vector-toc-numb">2</span>2019 <i>Forbes</i> list</div>
</a>
<ul class="vector-toc-list" id="toc-2019_Forbes_list-sublist">
</ul>
</li>
<li class="vector-toc-list-item vector-toc-level-1 vector-toc-list-item-expanded" id
="toc-See_also">
<a class="vector-toc-link" href="#See_also">
<div class="vector-toc-text">
<span class="vector-toc-numb">3</span>See also</div>
</a>
<ul class="vector-toc-list" id="toc-See_also-sublist">
</ul>
</li>
<li class="vector-toc-list-item vector-toc-level-1 vector-toc-list-item-expanded" id
="toc-References">
<a class="vector-toc-link" href="#References">
<div class="vector-toc-text">
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 8/48
<span class="vector-toc-numb">4</span>References</div>
</a>
<ul class="vector-toc-list" id="toc-References-sublist">
</ul>
</li>
</ul>
</div>
</div>
</nav>
<div class="mw-content-container">
<main class="mw-body" id="content" role="main">
<header class="mw-body-header vector-page-titlebar">
<label aria-controls="vector-toc" class="cdx-button cdx-button--fake-button cdx-butto
n--fake-button--enabled cdx-button--weight-quiet vector-button-flush-left cdx-button-
-icon-only" for="vector-toc-collapsed-checkbox" id="vector-toc-collapsed-button" role
="button" tabindex="0" title="Table of Contents">
<span class="vector-icon mw-ui-icon-wikimedia-listBullet"></span>
<span>Toggle the table of contents</span>
</label>
<nav aria-label="Contents" class="vector-toc-landmark" role="navigation">
<div class="vector-dropdown vector-page-titlebar-toc vector-button-flush-left" id="ve
ctor-page-titlebar-toc">
<input aria-haspopup="true" aria-label="Toggle the table of contents" class="vector-d
ropdown-checkbox" data-event-name="ui.dropdown-vector-page-titlebar-toc" id="vector-p
age-titlebar-toc-checkbox" role="button" type="checkbox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet cdx-button--icon-only"
for="vector-page-titlebar-toc-checkbox" id="vector-page-titlebar-toc-label"><span cla
ss="vector-icon mw-ui-icon-listBullet mw-ui-icon-wikimedia-listBullet"></span>
<span class="vector-dropdown-label-text">Toggle the table of contents</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-unpinned-container" id="vector-page-titlebar-toc-unpinned-containe
r">
</div>
</div>
</div>
</nav>
<h1 class="firstHeading mw-first-heading" id="firstHeading"><span class="mw-page-titl
e-main">List of largest companies in Canada</span></h1>
<div class="vector-dropdown mw-portlet mw-portlet-lang" id="p-lang-btn">
<input aria-haspopup="true" aria-label="Go to an article in another language. Availab
le in 2 languages" class="vector-dropdown-checkbox mw-interlanguage-selector" data-ev
ent-name="ui.dropdown-p-lang-btn" id="p-lang-btn-checkbox" role="button" type="checkb
ox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet cdx-button--action-pro
gressive mw-portlet-lang-heading-2" for="p-lang-btn-checkbox" id="p-lang-btn-label"><
span class="vector-icon mw-ui-icon-language-progressive mw-ui-icon-wikimedia-language
-progressive"></span>
<span class="vector-dropdown-label-text">2 languages</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="interlanguage-link interwiki-ar mw-list-item"><a class="interlanguage-link
-target" href="https://ar.wikipedia.org/wiki/%D9%82%D8%A7%D8%A6%D9%85%D8%A9_%D8%A3%D
9%83%D8%A8%D8%B1_%D8%A7%D9%84%D8%B4%D8%B1%D9%83%D8%A7%D8%AA_%D9%81%D9%8A_%D9%83%D9%8
6%D8%AF%D8%A7" hreflang="ar" lang="ar" title="كندا في الشركات أكبر قائمة – Arabic"><span>العربية
</span></a></li><li class="interlanguage-link interwiki-de mw-list-item"><a class="in
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 9/48
terlanguage-link-target" href="https://de.wikipedia.org/wiki/Liste_der_gr%C3%B6%C3%9F
ten_Unternehmen_in_Kanada" hreflang="de" lang="de" title="Liste der größten Unternehm
en in Kanada – German"><span>Deutsch</span></a></li>
</ul>
<div class="after-portlet after-portlet-lang"><span class="wb-langlinks-edit wb-langl
inks-link"><a class="wbc-editpage" href="https://www.wikidata.org/wiki/Special:Entity
Page/Q1371361#sitelinks-wikipedia" title="Edit interlanguage links">Edit links</a></s
pan></div>
</div>
</div>
</div>
</header>
<div class="vector-page-toolbar">
<div class="vector-page-toolbar-container">
<div id="left-navigation">
<nav aria-label="Namespaces">
<div class="vector-menu vector-menu-tabs mw-portlet mw-portlet-associated-pages" id
="p-associated-pages">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="selected vector-tab-noicon mw-list-item" id="ca-nstab-main"><a accesskey
="c" href="/wiki/List_of_largest_companies_in_Canada" title="View the content page
[c]"><span>Article</span></a></li><li class="vector-tab-noicon mw-list-item" id="ca-t
alk"><a accesskey="t" href="/wiki/Talk:List_of_largest_companies_in_Canada" rel="disc
ussion" title="Discuss improvements to the content page [t]"><span>Talk</span></a></l
i>
</ul>
</div>
</div>
<div class="vector-dropdown emptyPortlet" id="p-variants">
<input aria-haspopup="true" aria-label="Change language variant" class="vector-dropdo
wn-checkbox" data-event-name="ui.dropdown-p-variants" id="p-variants-checkbox" role
="button" type="checkbox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet" for="p-variants-check
box" id="p-variants-label"><span class="vector-dropdown-label-text">English</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-menu mw-portlet mw-portlet-variants emptyPortlet" id="p-variants">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
</ul>
</div>
</div>
</div>
</div>
</nav>
</div>
<div class="vector-collapsible" id="right-navigation">
<nav aria-label="Views">
<div class="vector-menu vector-menu-tabs mw-portlet mw-portlet-views" id="p-views">
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="selected vector-tab-noicon mw-list-item" id="ca-view"><a href="/wiki/List_
of_largest_companies_in_Canada"><span>Read</span></a></li><li class="vector-tab-noico
n mw-list-item" id="ca-edit"><a accesskey="e" href="/w/index.php?title=List_of_larges
t_companies_in_Canada&amp;action=edit" title="Edit this page [e]"><span>Edit</span></
a></li><li class="vector-tab-noicon mw-list-item" id="ca-history"><a accesskey="h" hr
ef="/w/index.php?title=List_of_largest_companies_in_Canada&amp;action=history" title
="Past revisions of this page [h]"><span>View history</span></a></li>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 10/48
</ul>
</div>
</div>
</nav>
<nav aria-label="More options" class="vector-page-tools-landmark">
<div class="vector-dropdown vector-page-tools-dropdown" id="vector-page-tools-dropdow
n">
<input aria-haspopup="true" aria-label="Tools" class="vector-dropdown-checkbox" dataevent-name="ui.dropdown-vector-page-tools-dropdown" id="vector-page-tools-dropdown-ch
eckbox" role="button" type="checkbox"/>
<label aria-hidden="true" class="vector-dropdown-label cdx-button cdx-button--fake-bu
tton cdx-button--fake-button--enabled cdx-button--weight-quiet" for="vector-page-tool
s-dropdown-checkbox" id="vector-page-tools-dropdown-label"><span class="vector-dropdo
wn-label-text">Tools</span>
</label>
<div class="vector-dropdown-content">
<div class="vector-unpinned-container" id="vector-page-tools-unpinned-container">
<div class="vector-page-tools vector-pinnable-element" id="vector-page-tools">
<div class="vector-pinnable-header vector-page-tools-pinnable-header vector-pinnableheader-unpinned" data-feature-name="page-tools-pinned" data-pinnable-element-id="vect
or-page-tools" data-pinned-container-id="vector-page-tools-pinned-container" data-unp
inned-container-id="vector-page-tools-unpinned-container">
<div class="vector-pinnable-header-label">Tools</div>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-pin-butto
n" data-event-name="pinnable-header.vector-page-tools.pin">move to sidebar</button>
<button class="vector-pinnable-header-toggle-button vector-pinnable-header-unpin-butt
on" data-event-name="pinnable-header.vector-page-tools.unpin">hide</button>
</div>
<div class="vector-menu mw-portlet mw-portlet-cactions emptyPortlet vector-has-collap
sible-items" id="p-cactions" title="More options">
<div class="vector-menu-heading">
Actions
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="selected vector-more-collapsible-item mw-list-item" id="ca-more-view"><a h
ref="/wiki/List_of_largest_companies_in_Canada"><span>Read</span></a></li><li class
="vector-more-collapsible-item mw-list-item" id="ca-more-edit"><a href="/w/index.php?
title=List_of_largest_companies_in_Canada&amp;action=edit"><span>Edit</span></a></li>
<li class="vector-more-collapsible-item mw-list-item" id="ca-more-history"><a href="/
w/index.php?title=List_of_largest_companies_in_Canada&amp;action=history"><span>View
history</span></a></li>
</ul>
</div>
</div>
<div class="vector-menu mw-portlet mw-portlet-tb" id="p-tb">
<div class="vector-menu-heading">
General
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="mw-list-item" id="t-whatlinkshere"><a accesskey="j" href="/wiki/Special:Wh
atLinksHere/List_of_largest_companies_in_Canada" title="List of all English Wikipedia
pages containing links to this page [j]"><span>What links here</span></a></li><li cla
ss="mw-list-item" id="t-recentchangeslinked"><a accesskey="k" href="/wiki/Special:Rec
entChangesLinked/List_of_largest_companies_in_Canada" rel="nofollow" title="Recent ch
anges in pages linked from this page [k]"><span>Related changes</span></a></li><li cl
ass="mw-list-item" id="t-upload"><a accesskey="u" href="/wiki/Wikipedia:File_Upload_W
izard" title="Upload files [u]"><span>Upload file</span></a></li><li class="mw-list-i
tem" id="t-specialpages"><a accesskey="q" href="/wiki/Special:SpecialPages" title="A
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 11/48
list of all special pages [q]"><span>Special pages</span></a></li><li class="mw-listitem" id="t-permalink"><a href="/w/index.php?title=List_of_largest_companies_in_Canad
a&amp;oldid=1168712460" title="Permanent link to this revision of this page"><span>Pe
rmanent link</span></a></li><li class="mw-list-item" id="t-info"><a href="/w/index.ph
p?title=List_of_largest_companies_in_Canada&amp;action=info" title="More information
about this page"><span>Page information</span></a></li><li class="mw-list-item" id="t
-cite"><a href="/w/index.php?title=Special:CiteThisPage&amp;page=List_of_largest_comp
anies_in_Canada&amp;id=1168712460&amp;wpFormIdentifier=titleform" title="Information
on how to cite this page"><span>Cite this page</span></a></li><li class="mw-list-ite
m" id="t-wikibase"><a accesskey="g" href="https://www.wikidata.org/wiki/Special:Entit
yPage/Q1371361" title="Structured data on this page hosted by Wikidata [g]"><span>Wik
idata item</span></a></li>
</ul>
</div>
</div>
<div class="vector-menu mw-portlet mw-portlet-coll-print_export" id="p-coll-print_exp
ort">
<div class="vector-menu-heading">
Print/export
</div>
<div class="vector-menu-content">
<ul class="vector-menu-content-list">
<li class="mw-list-item" id="coll-download-as-rl"><a href="/w/index.php?title=Specia
l:DownloadAsPdf&amp;page=List_of_largest_companies_in_Canada&amp;action=show-download
-screen" title="Download this page as a PDF file"><span>Download as PDF</span></a></l
i><li class="mw-list-item" id="t-print"><a accesskey="p" href="/w/index.php?title=Lis
t_of_largest_companies_in_Canada&amp;printable=yes" title="Printable version of this
page [p]"><span>Printable version</span></a></li>
</ul>
</div>
</div>
</div>
</div>
</div>
</div>
</nav>
</div>
</div>
</div>
<div class="vector-column-end">
<nav aria-label="More options" class="vector-page-tools-landmark vector-sticky-pinned
-container">
<div class="vector-pinned-container" id="vector-page-tools-pinned-container">
</div>
</nav>
</div>
<div aria-labelledby="firstHeading" class="vector-body" data-mw-ve-target-container
="" id="bodyContent">
<div class="vector-body-before-content">
<div class="mw-indicators">
</div>
<div class="noprint" id="siteSub">From Wikipedia, the free encyclopedia</div>
</div>
<div id="contentSub"><div id="mw-content-subtitle"></div></div>
<div class="mw-body-content mw-content-ltr" dir="ltr" id="mw-content-text" lang="en">
<div class="mw-parser-output"><p>
This article lists the largest <a href="/wiki/Company" title="Company">companies</a>
in <a href="/wiki/Canada" title="Canada">Canada</a> in terms of their <a href="/wiki/
Revenue" title="Revenue">revenue</a>, <a class="mw-redirect" href="/wiki/Net_profit"
title="Net profit">net profit</a> and <a class="mw-redirect" href="/wiki/Total_asset
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 12/48
s" title="Total assets">total assets</a>, according to the American business magazine
s <i><a href="/wiki/Fortune_(magazine)" title="Fortune (magazine)">Fortune</a></i> an
d <i><a href="/wiki/Forbes" title="Forbes">Forbes</a></i>. 
</p>
<meta property="mw:PageProp/toc"/>
<h2><span class="mw-headline" id="2023_Fortune_list">2023 <i>Fortune</i> list</span><
span class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/
index.php?title=List_of_largest_companies_in_Canada&amp;action=edit&amp;section=1" ti
tle="Edit section: 2023 Fortune list">edit</a><span class="mw-editsection-bracket">]
</span></span></h2>
<p>This list displays all 14 Canadian companies in the <a href="/wiki/Fortune_Global_
500" title="Fortune Global 500">Fortune Global 500</a>, which ranks the world's large
st companies by annual revenue. The figures below are given in millions of <a class
="mw-redirect" href="/wiki/US_dollar" title="US dollar">US dollars</a> and are for th
e <a href="/wiki/Fiscal_year" title="Fiscal year">fiscal year</a> 2022.<sup class="re
ference" id="cite_ref-1"><a href="#cite_note-1">[1]</a></sup> Also listed are the hea
dquarters location, net profit, number of employees worldwide and industry sector of
each company.
</p>
<table class="wikitable sortable">
<tbody><tr>
<th>Rank
</th>
<th>Fortune 500<br/>rank
</th>
<th>Name
</th>
<th>Industry
</th>
<th>Revenue<br/><small>(USD millions)</small>
</th>
<th>Profits<br/><small>(USD millions)</small>
</th>
<th>Employees
</th>
<th>Headquarters
</th></tr>
<tr>
<td>1
</td>
<td>117
</td>
<td><a class="mw-redirect" href="/wiki/Brookfield_Asset_Management" title="Brookfield
Asset Management">Brookfield Asset Management</a>
</td>
<td><a href="/wiki/Finance" title="Finance">Finance</a>
</td>
<td style="text-align:center;">92,769
</td>
<td style="text-align:center;">2,056
</td>
<td style="text-align:center;">202,500
</td>
<td><a href="/wiki/Toronto" title="Toronto">Toronto</a>
</td></tr>
<tr>
<td>2
</td>
<td>214
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 13/48
<td><a href="/wiki/Alimentation_Couche-Tard" title="Alimentation Couche-Tard">Aliment
ation Couche-Tard</a>
</td>
<td><a href="/wiki/Retail" title="Retail">Retail</a>
</td>
<td style="text-align:center;">62,810
</td>
<td style="text-align:center;">2,683
</td>
<td style="text-align:center;">122,000
</td>
<td><a href="/wiki/Laval,_Quebec" title="Laval, Quebec">Laval</a>
</td></tr>
<tr>
<td>3
</td>
<td>270
</td>
<td><a href="/wiki/Royal_Bank_of_Canada" title="Royal Bank of Canada">Royal Bank of C
anada</a>
</td>
<td><a class="mw-redirect" href="/wiki/Banking" title="Banking">Banking</a>
</td>
<td style="text-align:center;">52,062
</td>
<td style="text-align:center;">12,265
</td>
<td style="text-align:center;">91,427
</td>
<td>Toronto
</td></tr>
<tr>
<td>4
</td>
<td>277
</td>
<td><a href="/wiki/Cenovus_Energy" title="Cenovus Energy">Cenovus Energy</a>
</td>
<td><a class="mw-redirect" href="/wiki/Oil_and_Gas" title="Oil and Gas">Oil and Gas</
a>
</td>
<td style="text-align:center;">51,406
</td>
<td style="text-align:center;">4,956
</td>
<td style="text-align:center;">5,998
</td>
<td><a href="/wiki/Calgary" title="Calgary">Calgary</a>
</td></tr>
<tr>
<td>5
</td>
<td>294
</td>
<td><a href="/wiki/Toronto-Dominion_Bank" title="Toronto-Dominion Bank">Toronto-Domin
ion Bank</a>
</td>
<td>Banking
</td>
<td style="text-align:center;">48,700
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 14/48
</td>
<td style="text-align:center;">13,535
</td>
<td style="text-align:center;">94,945
</td>
<td>Toronto
</td></tr>
<tr>
<td>6
</td>
<td>327
</td>
<td><a href="/wiki/Suncor_Energy" title="Suncor Energy">Suncor Energy</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">44,928
</td>
<td style="text-align:center;">6,975
</td>
<td style="text-align:center;">16,558
</td>
<td>Calgary
</td></tr>
<tr>
<td>7
</td>
<td>336
</td>
<td><a href="/wiki/George_Weston_Limited" title="George Weston Limited">George Weston
Limited</a>
</td>
<td>Retail
</td>
<td style="text-align:center;">43,838
</td>
<td style="text-align:center;">1,396
</td>
<td style="text-align:center;">221,285
</td>
<td>Toronto
</td></tr>
<tr>
<td>8
</td>
<td>365
</td>
<td><a href="/wiki/Enbridge" title="Enbridge">Enbridge</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">40,964
</td>
<td style="text-align:center;">2,308
</td>
<td style="text-align:center;">12,050
</td>
<td>Calgary
</td></tr>
<tr>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 15/48
<td>9
</td>
<td>392
</td>
<td><a href="/wiki/Nutrien" title="Nutrien">Nutrien</a>
</td>
<td><a href="/wiki/Agriculture" title="Agriculture">Agriculture</a>
</td>
<td style="text-align:center;">37,884
</td>
<td style="text-align:center;">7,660
</td>
<td style="text-align:center;">24,700
</td>
<td><a href="/wiki/Saskatoon" title="Saskatoon">Saskatoon</a>
</td></tr>
<tr>
<td>10
</td>
<td>394
</td>
<td><a href="/wiki/Magna_International" title="Magna International">Magna Internation
al</a>
</td>
<td><a class="mw-redirect" href="/wiki/Automotive_parts" title="Automotive parts">Aut
omotive parts</a>
</td>
<td style="text-align:center;">37,840
</td>
<td style="text-align:center;">592
</td>
<td style="text-align:center;">158,000
</td>
<td><a href="/wiki/Aurora,_Ontario" title="Aurora, Ontario">Aurora</a>
</td></tr>
<tr>
<td>11
</td>
<td>399
</td>
<td><a href="/wiki/Power_Corporation_of_Canada" title="Power Corporation of Canada">P
ower Corporation of Canada</a>
</td>
<td>Finance
</td>
<td style="text-align:center;">37,419
</td>
<td style="text-align:center;">1,510
</td>
<td style="text-align:center;">37,300
</td>
<td><a href="/wiki/Montreal" title="Montreal">Montreal</a>
</td></tr>
<tr>
<td>12
</td>
<td>415
</td>
<td><a href="/wiki/Scotiabank" title="Scotiabank">Scotiabank</a>
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 16/48
<td>Banking
</td>
<td style="text-align:center;">36,390
</td>
<td style="text-align:center;">7,701
</td>
<td style="text-align:center;">90,979
</td>
<td>Toronto
</td></tr>
<tr>
<td>13
</td>
<td>433
</td>
<td><a href="/wiki/Bank_of_Montreal" title="Bank of Montreal">Bank of Montreal</a>
</td>
<td>Banking
</td>
<td style="text-align:center;">34,730
</td>
<td style="text-align:center;">10,513
</td>
<td style="text-align:center;">46,722
</td>
<td>Montreal
</td></tr>
<tr>
<td>14
</td>
<td>471
</td>
<td><a href="/wiki/Canadian_Natural_Resources" title="Canadian Natural Resources">Can
adian Natural Resources</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">32,503
</td>
<td style="text-align:center;">8,404
</td>
<td style="text-align:center;">10,035
</td>
<td>Calgary
</td></tr></tbody></table>
<h2><span class="mw-headline" id="2019_Forbes_list">2019 <i>Forbes</i> list</span><sp
an class="mw-editsection"><span class="mw-editsection-bracket">[</span><a href="/w/in
dex.php?title=List_of_largest_companies_in_Canada&amp;action=edit&amp;section=2" titl
e="Edit section: 2019 Forbes list">edit</a><span class="mw-editsection-bracket">]</sp
an></span></h2>
<p>This list is based on the <a href="/wiki/Forbes_Global_2000" title="Forbes Global
2000">Forbes Global 2000</a>, which ranks the world's 2,000 largest <a href="/wiki/Pu
blic_company" title="Public company">publicly traded companies</a>. The <i>Forbes</i>
list takes into account a multitude of factors, including the revenue, net profit, <a
class="mw-redirect" href="/wiki/Total_assets" title="Total assets">total assets</a> a
nd <a href="/wiki/Market_value" title="Market value">market value</a> of each compan
y; each factor is given a weighted rank in terms of importance when considering the o
verall ranking. The location of each company's headquarters and its industry sector a
re also listed in the table below.The figures are in billions of US dollars and are f
or the year 2018. All 56 companies from Canada are listed.<sup class="reference" id
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 17/48
="cite_ref-2"><a href="#cite_note-2">[2]</a></sup>
</p>
<table class="wikitable sortable" style="text-align:right;">
<tbody><tr>
<th align="center">Rank
</th>
<th align="center">Forbes <br/>2000 rank
</th>
<th align="center">Name
</th>
<th align="center">Headquarters
</th>
<th align="center">Revenue<br/>(billions <br/>US$)
</th>
<th align="center">Profit<br/>(billions <br/>US$)
</th>
<th align="center">Assets<br/>(billions <br/>US$)
</th>
<th align="center">Value<br/>(billions <br/>US$)
</th>
<th align="center">Industry
</th></tr>
<tr>
<td>1
</td>
<td>41
</td>
<td align="left"><a href="/wiki/Royal_Bank_of_Canada" title="Royal Bank of Canada">Ro
yal Bank of Canada</a>
</td>
<td align="left">Toronto
</td>
<td>46.3
</td>
<td>9.6
</td>
<td>1,040.3
</td>
<td>114.9
</td>
<td align="left">Banking
</td></tr>
<tr>
<td>2
</td>
<td>46
</td>
<td align="left"><a href="/wiki/Toronto-Dominion_Bank" title="Toronto-Dominion Bank">
Toronto-Dominion Bank</a>
</td>
<td align="left">Toronto
</td>
<td>42.5
</td>
<td>8.7
</td>
<td>1,007.0
</td>
<td>103.8
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 18/48
<td align="left">Banking
</td></tr>
<tr>
<td>3
</td>
<td>87
</td>
<td align="left"><a href="/wiki/Scotiabank" title="Scotiabank">Scotiabank</a>
</td>
<td align="left">Toronto
</td>
<td>32.4
</td>
<td>6.4
</td>
<td>787.5
</td>
<td>67.1
</td>
<td align="left">Banking
</td></tr>
<tr>
<td>4
</td>
<td>118
</td>
<td align="left"><a class="mw-redirect" href="/wiki/Brookfield_Asset_Management" titl
e="Brookfield Asset Management">Brookfield Asset Management</a>
</td>
<td align="left">Toronto
</td>
<td>57.6
</td>
<td>3.6
</td>
<td>256.3
</td>
<td>46.0
</td>
<td align="left">Finance
</td></tr>
<tr>
<td>5
</td>
<td>134
</td>
<td align="left"><a href="/wiki/Bank_of_Montreal" title="Bank of Montreal">Bank of Mo
ntreal</a>
</td>
<td align="left">Montreal
</td>
<td>26.2
</td>
<td>4.6
</td>
<td>614.2
</td>
<td>50.4
</td>
<td align="left">Banking
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 19/48
</td></tr>
<tr>
<td>6
</td>
<td>166
</td>
<td align="left"><a href="/wiki/Manulife" title="Manulife">Manulife</a>
</td>
<td align="left">Toronto
</td>
<td>28.4
</td>
<td>3.7
</td>
<td>517.8
</td>
<td>36.2
</td>
<td align="left">Insurance
</td></tr>
<tr>
<td>7
</td>
<td>174
</td>
<td align="left"><a href="/wiki/Enbridge" title="Enbridge">Enbridge</a>
</td>
<td align="left">Calgary
</td>
<td>36.1
</td>
<td>2.2
</td>
<td>122.2
</td>
<td>75.3
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>8
</td>
<td>190
</td>
<td align="left"><a href="/wiki/Canadian_Imperial_Bank_of_Commerce" title="Canadian I
mperial Bank of Commerce">Canadian Imperial Bank of Commerce</a>
</td>
<td align="left">Toronto
</td>
<td>20.2
</td>
<td>3.9
</td>
<td>486.0
</td>
<td>36.8
</td>
<td align="left">Banking
</td></tr>
<tr>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 20/48
<td>9
</td>
<td>229
</td>
<td align="left"><a href="/wiki/Suncor_Energy" title="Suncor Energy">Suncor Energy</a
>
</td>
<td align="left">Calgary
</td>
<td>29.7
</td>
<td>2.5
</td>
<td>65.6
</td>
<td>52.6
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>10
</td>
<td>273
</td>
<td align="left"><a href="/wiki/Sun_Life_Financial" title="Sun Life Financial">Sun Li
fe Financial</a>
</td>
<td align="left">Toronto
</td>
<td>23.4
</td>
<td>2.0
</td>
<td>196.0
</td>
<td>24.5
</td>
<td align="left">Insurance
</td></tr>
<tr>
<td>11
</td>
<td>341
</td>
<td align="left"><a href="/wiki/Bell_Canada" title="Bell Canada">Bell Canada</a>
</td>
<td align="left">Montreal
</td>
<td>18.1
</td>
<td>2.3
</td>
<td>41.8
</td>
<td>40.9
</td>
<td align="left"><a class="mw-redirect" href="/wiki/Telecommunication" title="Telecom
munication">Telecommunication</a>
</td></tr>
<tr>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 21/48
<td>12
</td>
<td>342
</td>
<td align="left"><a href="/wiki/Canadian_Natural_Resources" title="Canadian Natural R
esources">Canadian Natural Resources</a>
</td>
<td align="left">Calgary
</td>
<td>16.2
</td>
<td>2.0
</td>
<td>53.9
</td>
<td>37.6
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>13
</td>
<td>346
</td>
<td align="left"><a href="/wiki/TC_Energy" title="TC Energy">TC Energy</a>
</td>
<td align="left">Calgary
</td>
<td>10.3
</td>
<td>2.9
</td>
<td>72.4
</td>
<td>43.2
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>14
</td>
<td>364
</td>
<td align="left"><a href="/wiki/Alimentation_Couche-Tard" title="Alimentation CoucheTard">Alimentation Couche-Tard</a>
</td>
<td align="left">Laval
</td>
<td>59.7
</td>
<td>2.0
</td>
<td>22.2
</td>
<td>33.7
</td>
<td align="left"><a href="/wiki/Retail" title="Retail">Retail</a>
</td></tr>
<tr>
<td>15
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 22/48
</td>
<td>388
</td>
<td align="left"><a href="/wiki/Canadian_National_Railway" title="Canadian National R
ailway">Canadian National Railway</a>
</td>
<td align="left">Montreal
</td>
<td>11.0
</td>
<td>3.3
</td>
<td>30.5
</td>
<td>67.9
</td>
<td align="left"><a class="mw-redirect" href="/wiki/Transportation" title="Transporta
tion">Transportation</a>
</td></tr>
<tr>
<td>16
</td>
<td>397
</td>
<td align="left"><a href="/wiki/Power_Corporation_of_Canada" title="Power Corporation
of Canada">Power Corporation of Canada</a>
</td>
<td align="left">Montreal
</td>
<td>40.0
</td>
<td>1.0
</td>
<td>326.7
</td>
<td>11.4
</td>
<td align="left">Finance
</td></tr>
<tr>
<td>17
</td>
<td>427
</td>
<td align="left"><a href="/wiki/Magna_International" title="Magna International">Magn
a International</a>
</td>
<td align="left">Aurora
</td>
<td>40.8
</td>
<td>2.3
</td>
<td>25.9
</td>
<td>18.3
</td>
<td align="left">Automotive parts
</td></tr>
<tr>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 23/48
<td>18
</td>
<td>501
</td>
<td align="left"><a href="/wiki/National_Bank_of_Canada" title="National Bank of Cana
da">National Bank of Canada</a>
</td>
<td align="left">Montreal
</td>
<td>8.4
</td>
<td>1.7
</td>
<td>200.5
</td>
<td>15.9
</td>
<td align="left">Banking
</td></tr>
<tr>
<td>19
</td>
<td>566
</td>
<td align="left"><a href="/wiki/Rogers_Communications" title="Rogers Communications">
Rogers Communications</a>
</td>
<td align="left">Toronto
</td>
<td>11.6
</td>
<td>1.6
</td>
<td>23.4
</td>
<td>26.6
</td>
<td align="left">Telecommunication
</td></tr>
<tr>
<td>20
</td>
<td>623
</td>
<td align="left"><a href="/wiki/Teck_Resources" title="Teck Resources">Teck Resources
</a>
</td>
<td align="left"><a href="/wiki/Vancouver" title="Vancouver">Vancouver</a>
</td>
<td>9.7
</td>
<td>2.4
</td>
<td>29.0
</td>
<td>14.1
</td>
<td align="left">Mining
</td></tr>
<tr>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 24/48
<td>21
</td>
<td>625
</td>
<td align="left"><a href="/wiki/Telus" title="Telus">Telus</a>
</td>
<td align="left">Vancouver
</td>
<td>10.9
</td>
<td>1.2
</td>
<td>24.2
</td>
<td>22.4
</td>
<td align="left">Telecommunication
</td></tr>
<tr>
<td>22
</td>
<td>674
</td>
<td align="left"><a href="/wiki/Husky_Energy" title="Husky Energy">Husky Energy</a>
</td>
<td align="left">Calgary
</td>
<td>17.1
</td>
<td>1.1
</td>
<td>26.6
</td>
<td>10.9
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>23
</td>
<td>678
</td>
<td align="left"><a href="/wiki/Nutrien" title="Nutrien">Nutrien</a>
</td>
<td align="left"><a href="/wiki/Saskatoon" title="Saskatoon">Saskatoon</a>
</td>
<td>19.6
</td>
<td>0.0
</td>
<td>45.5
</td>
<td>32.3
</td>
<td align="left"><a href="/wiki/Agriculture" title="Agriculture">Agriculture</a>
</td></tr>
<tr>
<td>24
</td>
<td>744
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 25/48
</td>
<td align="left"><a href="/wiki/George_Weston_Limited" title="George Weston Limited">
George Weston Limited</a>
</td>
<td align="left">Toronto
</td>
<td>37.5
</td>
<td>0.4
</td>
<td>32.1
</td>
<td>11.7
</td>
<td align="left">Retail
</td></tr>
<tr>
<td>25
</td>
<td>766
</td>
<td align="left"><a href="/wiki/Fairfax_Financial" title="Fairfax Financial">Fairfax
Financial</a>
</td>
<td align="left">Toronto
</td>
<td>18.2
</td>
<td>0.4
</td>
<td>64.4
</td>
<td>13.7
</td>
<td align="left">Insurance
</td></tr>
<tr>
<td>26
</td>
<td>771
</td>
<td align="left"><a href="/wiki/Fortis_Inc." title="Fortis Inc.">Fortis Inc.</a>
</td>
<td align="left"><a href="/wiki/St._John%27s,_Newfoundland_and_Labrador" title="St. J
ohn's, Newfoundland and Labrador">St. John's</a>
</td>
<td>6.5
</td>
<td>0.9
</td>
<td>39.9
</td>
<td>16.1
</td>
<td align="left"><a class="mw-redirect" href="/wiki/Utilities" title="Utilities">Util
ities</a>
</td></tr>
<tr>
<td>27
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 26/48
<td>828
</td>
<td align="left"><a href="/wiki/Canadian_Pacific_Railway" title="Canadian Pacific Rai
lway">Canadian Pacific Railway</a>
</td>
<td align="left">Calgary
</td>
<td>5.6
</td>
<td>1.5
</td>
<td>15.7
</td>
<td>30.3
</td>
<td align="left">Transportation
</td></tr>
<tr>
<td>28
</td>
<td>897
</td>
<td align="left"><a href="/wiki/Pembina_Pipeline" title="Pembina Pipeline">Pembina Pi
peline</a>
</td>
<td align="left">Calgary
</td>
<td>5.8
</td>
<td>1.0
</td>
<td>19.5
</td>
<td>19.0
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>29
</td>
<td>974
</td>
<td align="left"><a href="/wiki/CGI_Inc." title="CGI Inc.">CGI Inc.</a>
</td>
<td align="left">Montreal
</td>
<td>9.0
</td>
<td>0.9
</td>
<td>9.4
</td>
<td>19.5
</td>
<td align="left"><a class="mw-redirect" href="/wiki/IT_services" title="IT services">
IT services</a>
</td></tr>
<tr>
<td>30
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 27/48
<td>985
</td>
<td align="left"><a href="/wiki/Cenovus_Energy" title="Cenovus Energy">Cenovus Energy
</a>
</td>
<td align="left">Calgary
</td>
<td>16.1
</td>
<td>−2.2
</td>
<td>26.3
</td>
<td>12.4
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>31
</td>
<td>1035
</td>
<td align="left"><a href="/wiki/Thomson_Reuters" title="Thomson Reuters">Thomson Reut
ers</a>
</td>
<td align="left">Toronto
</td>
<td>5.5
</td>
<td>0.5
</td>
<td>17.0
</td>
<td>30.1
</td>
<td align="left"><a href="/wiki/Mass_media" title="Mass media">Media</a>
</td></tr>
<tr>
<td>32
</td>
<td>1043
</td>
<td align="left"><a href="/wiki/Intact_Financial" title="Intact Financial">Intact Fin
ancial</a>
</td>
<td align="left">Toronto
</td>
<td>8.0
</td>
<td>0.5
</td>
<td>20.2
</td>
<td>11.6
</td>
<td align="left">Insurance
</td></tr>
<tr>
<td>33
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 28/48
<td>1056
</td>
<td align="left"><a href="/wiki/Onex_Corporation" title="Onex Corporation">Onex Corpo
ration</a>
</td>
<td align="left">Toronto
</td>
<td>25.1
</td>
<td>−0.6
</td>
<td>45.4
</td>
<td>6.0
</td>
<td align="left">Finance
</td></tr>
<tr>
<td>34
</td>
<td>1072
</td>
<td align="left"><a href="/wiki/Restaurant_Brands_International" title="Restaurant Br
ands International">Restaurant Brands International</a>
</td>
<td align="left">Toronto
</td>
<td>5.4
</td>
<td>0.6
</td>
<td>20.1
</td>
<td>17.1
</td>
<td align="left"><a href="/wiki/Restaurant" title="Restaurant">Restaurants</a>
</td></tr>
<tr>
<td>35
</td>
<td>1084
</td>
<td align="left"><a href="/wiki/Barrick_Gold" title="Barrick Gold">Barrick Gold</a>
</td>
<td align="left">Toronto
</td>
<td>7.3
</td>
<td>−1.6
</td>
<td>22.6
</td>
<td>23.2
</td>
<td align="left">Mining
</td></tr>
<tr>
<td>36
</td>
<td>1134
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 29/48
</td>
<td align="left"><a href="/wiki/Encana" title="Encana">Encana</a>
</td>
<td align="left">Calgary
</td>
<td>5.5
</td>
<td>1.1
</td>
<td>15.3
</td>
<td>10.8
</td>
<td align="left">Oil and Gas
</td></tr>
<tr>
<td>37
</td>
<td>1158
</td>
<td align="left"><a href="/wiki/Saputo_Inc." title="Saputo Inc.">Saputo Inc.</a>
</td>
<td align="left">Montreal
</td>
<td>10.0
</td>
<td>0.6
</td>
<td>7.4
</td>
<td>13.3
</td>
<td align="left"><a href="/wiki/Food_processing" title="Food processing">Food process
ing</a>
</td></tr>
<tr>
<td>38
</td>
<td>1191
</td>
<td align="left"><a href="/wiki/IA_Financial_Group" title="IA Financial Group">IA Fin
ancial Group</a>
</td>
<td align="left"><a href="/wiki/Quebec_City" title="Quebec City">Quebec City</a>
</td>
<td>8.1
</td>
<td>0.5
</td>
<td>45.8
</td>
<td>4.2
</td>
<td align="left">Insurance
</td></tr>
<tr>
<td>39
</td>
<td>1275
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 30/48
<td align="left"><a href="/wiki/Waste_Connections" title="Waste Connections">Waste Co
nnections</a>
</td>
<td align="left"><a href="/wiki/Vaughan" title="Vaughan">Vaughan</a>
</td>
<td>4.9
</td>
<td>0.5
</td>
<td>12.6
</td>
<td>23.3
</td>
<td align="left"><a href="/wiki/Waste_management" title="Waste management">Waste mana
gement</a>
</td></tr>
<tr>
<td>40
</td>
<td>1292
</td>
<td align="left"><a href="/wiki/Bausch_Health" title="Bausch Health">Bausch Health</a
>
</td>
<td align="left"><a href="/wiki/Hatfield,_Hertfordshire" title="Hatfield, Hertfordshi
re">Laval</a>
</td>
<td>8.4
</td>
<td>−4.3
</td>
<td>32.5
</td>
<td>8.1
</td>
<td align="left">Pharmaceuticals
</td></tr>
<tr>
<td>41
</td>
<td>1310
</td>
<td align="left"><a href="/wiki/Bombardier_Inc." title="Bombardier Inc.">Bombardier I
nc.</a>
</td>
<td align="left">Montreal
</td>
<td>16.2
</td>
<td>0.2
</td>
<td>25.0
</td>
<td>5.0
</td>
<td align="left"><a href="/wiki/Aerospace" title="Aerospace">Aerospace</a> and <a hre
f="/wiki/Arms_industry" title="Arms industry">defense</a>
</td></tr>
<tr>
<td>42
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 31/48
</td>
<td>1317
</td>
<td align="left"><a href="/wiki/Metro_Inc." title="Metro Inc.">Metro Inc.</a>
</td>
<td align="left">Montreal
</td>
<td>12.2
</td>
<td>0.5
</td>
<td>8.0
</td>
<td>9.4
</td>
<td align="left">Retail
</td></tr>
<tr>
<td>43
</td>
<td>1341
</td>
<td align="left"><a href="/wiki/Emera" title="Emera">Emera</a>
</td>
<td align="left"><a href="/wiki/Halifax,_Nova_Scotia" title="Halifax, Nova Scotia">Ha
lifax</a>
</td>
<td>4.9
</td>
<td>0.6
</td>
<td>23.7
</td>
<td>8.9
</td>
<td align="left">Utilities
</td></tr>
<tr>
<td>44
</td>
<td>1365
</td>
<td align="left"><a href="/wiki/Alectra" title="Alectra">Alectra</a>
</td>
<td align="left"><a href="/wiki/Mississauga" title="Mississauga">Mississauga</a>
</td>
<td>4.8
</td>
<td>0.6
</td>
<td>19.4
</td>
<td>9.6
</td>
<td align="left">Utilities
</td></tr>
<tr>
<td>45
</td>
<td>1396
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 32/48
</td>
<td align="left"><a href="/wiki/Canadian_Tire" title="Canadian Tire">Canadian Tire</a
>
</td>
<td align="left">Toronto
</td>
<td>10.8
</td>
<td>0.5
</td>
<td>12.7
</td>
<td>6.9
</td>
<td align="left">Retail
</td></tr>
<tr>
<td>46
</td>
<td>1480
</td>
<td align="left"><a href="/wiki/Lululemon_Athletica" title="Lululemon Athletica">Lulu
lemon Athletica</a>
</td>
<td align="left">Vancouver
</td>
<td>3.3
</td>
<td>0.5
</td>
<td>2.1
</td>
<td>22.5
</td>
<td align="left">Retail
</td></tr>
<tr>
<td>47
</td>
<td>1578
</td>
<td align="left"><a href="/wiki/Air_Canada" title="Air Canada">Air Canada</a>
</td>
<td align="left">Montreal
</td>
<td>13.9
</td>
<td>0.1
</td>
<td>14.1
</td>
<td>6.6
</td>
<td align="left"><a href="/wiki/Airline" title="Airline">Airline</a>
</td></tr>
<tr>
<td>48
</td>
<td>1586
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 33/48
<td align="left"><a href="/wiki/First_Quantum_Minerals" title="First Quantum Mineral
s">First Quantum Minerals</a>
</td>
<td align="left">Toronto
</td>
<td>4.1
</td>
<td>0.4
</td>
<td>23.5
</td>
<td>8.2
</td>
<td align="left">Mining
</td></tr>
<tr>
<td>49
</td>
<td>1717
</td>
<td align="left"><a href="/wiki/Empire_Company" title="Empire Company">Empire Company
</a>
</td>
<td align="left"><a href="/wiki/Stellarton" title="Stellarton">Stellarton</a>
</td>
<td>19.0
</td>
<td>0.3
</td>
<td>7.1
</td>
<td>6.0
</td>
<td align="left"><a href="/wiki/Conglomerate_(company)" title="Conglomerate (compan
y)">Conglomerate</a>
</td></tr>
<tr>
<td>50
</td>
<td>1738
</td>
<td align="left"><a href="/wiki/Shopify" title="Shopify">Shopify</a>
</td>
<td align="left"><a href="/wiki/Ottawa" title="Ottawa">Ottawa</a>
</td>
<td>1.1
</td>
<td>−0.1
</td>
<td>2.3
</td>
<td>24.4
</td>
<td align="left"><a href="/wiki/E-commerce" title="E-commerce">E-commerce</a>
</td></tr>
<tr>
<td>51
</td>
<td>1744
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 34/48
<td align="left"><a href="/wiki/Advanz_Pharma" title="Advanz Pharma">Advanz Pharma</a
>
</td>
<td align="left">Mississauga
</td>
<td>0.5
</td>
<td>1.5
</td>
<td>1.8
</td>
<td>0.8
</td>
<td align="left">Pharmaceuticals
</td></tr>
<tr>
<td>52
</td>
<td>1757
</td>
<td align="left"><a href="/wiki/Constellation_Software" title="Constellation Softwar
e">Constellation Software</a>
</td>
<td align="left">Toronto
</td>
<td>3.1
</td>
<td>0.4
</td>
<td>2.9
</td>
<td>18.7
</td>
<td align="left">IT services
</td></tr>
<tr>
<td>53
</td>
<td>1805
</td>
<td align="left"><a href="/wiki/Canadian_Utilities" title="Canadian Utilities">Canadi
an Utilities</a>
</td>
<td align="left">Calgary
</td>
<td>3.4
</td>
<td>0.5
</td>
<td>16.0
</td>
<td>7.6
</td>
<td align="left">Utilities
</td></tr>
<tr>
<td>54
</td>
<td>1940
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 35/48
<td align="left"><a href="/wiki/Laurentian_Bank_of_Canada" title="Laurentian Bank of
Canada">Laurentian Bank of Canada</a>
</td>
<td align="left">Montreal
</td>
<td>1.4
</td>
<td>0.2
</td>
<td>34.4
</td>
<td>1.3
</td>
<td align="left">Banking
</td></tr>
<tr>
<td>55
</td>
<td>1975
</td>
<td align="left"><a href="/wiki/Goldcorp" title="Goldcorp">Goldcorp</a>
</td>
<td align="left">Vancouver
</td>
<td>3.0
</td>
<td>−4.2
</td>
<td>17.0
</td>
<td>9.4
</td>
<td align="left">Mining
</td></tr>
<tr>
<td>56
</td>
<td>1978
</td>
<td align="left"><a href="/wiki/CAPREIT" title="CAPREIT">CAPREIT</a>
</td>
<td align="left">Toronto
</td>
<td>0.5
</td>
<td>0.9
</td>
<td>7.9
</td>
<td>5.5
</td>
<td align="left">Real estate
</td></tr></tbody></table>
<h2><span class="mw-headline" id="See_also">See also</span><span class="mw-editsectio
n"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=List_of_l
argest_companies_in_Canada&amp;action=edit&amp;section=3" title="Edit section: See al
so">edit</a><span class="mw-editsection-bracket">]</span></span></h2>
<ul><li><a href="/wiki/List_of_companies_of_Canada" title="List of companies of Canad
a">List of companies of Canada</a></li>
<li><a href="/wiki/List_of_largest_public_companies_in_Canada_by_profit" title="List
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 36/48
of largest public companies in Canada by profit">List of largest public companies in
Canada by profit</a></li>
<li><a href="/wiki/List_of_largest_companies_by_revenue" title="List of largest compa
nies by revenue">List of largest companies by revenue</a></li>
<li><a href="/wiki/List_of_the_largest_trading_partners_of_Canada" title="List of the
largest trading partners of Canada">List of the largest trading partners of Canada</a
></li></ul>
<h2><span class="mw-headline" id="References">References</span><span class="mw-editse
ction"><span class="mw-editsection-bracket">[</span><a href="/w/index.php?title=List_
of_largest_companies_in_Canada&amp;action=edit&amp;section=4" title="Edit section: Re
ferences">edit</a><span class="mw-editsection-bracket">]</span></span></h2>
<style data-mw-deduplicate="TemplateStyles:r1011085734">.mw-parser-output .reflist{fo
nt-size:90%;margin-bottom:0.5em;list-style-type:decimal}.mw-parser-output .reflist .r
eferences{font-size:100%;margin-bottom:0;list-style-type:inherit}.mw-parser-output .r
eflist-columns-2{column-width:30em}.mw-parser-output .reflist-columns-3{column-width:
25em}.mw-parser-output .reflist-columns{margin-top:0.3em}.mw-parser-output .reflist-c
olumns ol{margin-top:0}.mw-parser-output .reflist-columns li{page-break-inside:avoid;
break-inside:avoid-column}.mw-parser-output .reflist-upper-alpha{list-style-type:uppe
r-alpha}.mw-parser-output .reflist-upper-roman{list-style-type:upper-roman}.mw-parser
-output .reflist-lower-alpha{list-style-type:lower-alpha}.mw-parser-output .reflist-l
ower-greek{list-style-type:lower-greek}.mw-parser-output .reflist-lower-roman{list-st
yle-type:lower-roman}</style><div class="reflist">
<div class="mw-references-wrap"><ol class="references">
<li id="cite_note-1"><span class="mw-cite-backlink"><b><a href="#cite_ref-1">^</a></b
></span> <span class="reference-text"><style data-mw-deduplicate="TemplateStyles:r113
3582631">.mw-parser-output cite.citation{font-style:inherit;word-wrap:break-word}.mwparser-output .citation q{quotes:"\"""\"""'""'"}.mw-parser-output .citation:target{ba
ckground-color:rgba(0,127,255,0.133)}.mw-parser-output .id-lock-free a,.mw-parser-out
put .citation .cs1-lock-free a{background:url("//upload.wikimedia.org/wikipedia/commo
ns/6/65/Lock-green.svg")right 0.1em center/9px no-repeat}.mw-parser-output .id-lock-l
imited a,.mw-parser-output .id-lock-registration a,.mw-parser-output .citation .cs1-l
ock-limited a,.mw-parser-output .citation .cs1-lock-registration a{background:url("//
upload.wikimedia.org/wikipedia/commons/d/d6/Lock-gray-alt-2.svg")right 0.1em center/9
px no-repeat}.mw-parser-output .id-lock-subscription a,.mw-parser-output .citation .c
s1-lock-subscription a{background:url("//upload.wikimedia.org/wikipedia/commons/a/aa/
Lock-red-alt-2.svg")right 0.1em center/9px no-repeat}.mw-parser-output .cs1-ws-icon a
{background:url("//upload.wikimedia.org/wikipedia/commons/4/4c/Wikisource-logo.svg")r
ight 0.1em center/12px no-repeat}.mw-parser-output .cs1-code{color:inherit;backgroun
d:inherit;border:none;padding:inherit}.mw-parser-output .cs1-hidden-error{display:non
e;color:#d33}.mw-parser-output .cs1-visible-error{color:#d33}.mw-parser-output .cs1-m
aint{display:none;color:#3a3;margin-left:0.3em}.mw-parser-output .cs1-format{font-siz
e:95%}.mw-parser-output .cs1-kern-left{padding-left:0.2em}.mw-parser-output .cs1-kern
-right{padding-right:0.2em}.mw-parser-output .citation .mw-selflink{font-weight:inher
it}</style><cite class="citation web cs1"><a class="external text" href="https://fort
une.com/global500/2019/" rel="nofollow">"Global 500"</a>. <i>Fortune</i><span class
="reference-accessdate">. Retrieved <span class="nowrap">2019-07-25</span></span>.</c
ite><span class="Z3988" title="ctx_ver=Z39.88-2004&amp;rft_val_fmt=info%3Aofi%2Ffmt%3
Akev%3Amtx%3Ajournal&amp;rft.genre=unknown&amp;rft.jtitle=Fortune&amp;rft.atitle=Glob
al+500&amp;rft_id=https%3A%2F%2Ffortune.com%2Fglobal500%2F2019%2F&amp;rfr_id=info%3As
id%2Fen.wikipedia.org%3AList+of+largest+companies+in+Canada"></span></span>
</li>
<li id="cite_note-2"><span class="mw-cite-backlink"><b><a href="#cite_ref-2">^</a></b
></span> <span class="reference-text"><link href="mw-data:TemplateStyles:r1133582631"
rel="mw-deduplicated-inline-style"/><cite class="citation web cs1"><a class="external
text" href="https://www.forbes.com/global2000/" rel="nofollow">"The World's Largest P
ublic Companies"</a>. <i>Forbes</i><span class="reference-accessdate">. Retrieved <sp
an class="nowrap">2019-07-25</span></span>.</cite><span class="Z3988" title="ctx_ver=
Z39.88-2004&amp;rft_val_fmt=info%3Aofi%2Ffmt%3Akev%3Amtx%3Ajournal&amp;rft.genre=unkn
own&amp;rft.jtitle=Forbes&amp;rft.atitle=The+World%27s+Largest+Public+Companies&amp;r
ft_id=https%3A%2F%2Fwww.forbes.com%2Fglobal2000%2F&amp;rfr_id=info%3Asid%2Fen.wikiped
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 37/48
ia.org%3AList+of+largest+companies+in+Canada"></span></span>
</li>
</ol></div></div>
<!-- 
NewPP limit report
Parsed by mw2375
Cached time: 20230804142543
Cache expiry: 1814400
Reduced expiry: false
Complications: [vary‐revision‐sha1, show‐toc]
CPU time usage: 0.135 seconds
Real time usage: 0.182 seconds
Preprocessor visited node count: 445/1000000
Post‐expand include size: 3457/2097152 bytes
Template argument size: 298/2097152 bytes
Highest expansion depth: 9/100
Expensive parser function count: 0/500
Unstrip recursion depth: 1/20
Unstrip post‐expand size: 5948/5000000 bytes
Lua time usage: 0.060/10.000 seconds
Lua memory usage: 2515403/52428800 bytes
Number of Wikibase entities loaded: 0/400
-->
<!--
Transclusion expansion time report (%,ms,calls,template)
100.00% 133.419 1 -total
59.39% 79.234 1 Template:Reflist
49.57% 66.142 2 Template:Cite_web
39.48% 52.674 1 Template:Short_description
21.06% 28.096 2 Template:Pagetype
 8.81% 11.752 3 Template:Main_other
 7.41% 9.886 1 Template:SDcat
 3.34% 4.456 1 Template:Short_description/lowercasecheck
 1.55% 2.065 1 Template:First_word
-->
<!-- Saved in parser cache with key enwiki:pcache:idhash:61383406-0!canonical and tim
estamp 20230804142543 and revision id 1168712460. Rendering was triggered because: pa
ge-view
-->
</div><!--esi <esi:include src="/esitest-fa8a495983347898/content" /> --><noscript><i
mg alt="" height="1" src="//en.wikipedia.org/wiki/Special:CentralAutoLogin/start?type
=1x1" style="border: none; position: absolute;" title="" width="1"/></noscript>
<div class="printfooter" data-nosnippet="">Retrieved from "<a dir="ltr" href="http
s://en.wikipedia.org/w/index.php?title=List_of_largest_companies_in_Canada&amp;oldid=
1168712460">https://en.wikipedia.org/w/index.php?title=List_of_largest_companies_in_C
anada&amp;oldid=1168712460</a>"</div></div>
<div class="catlinks" data-mw="interface" id="catlinks"><div class="mw-normal-catlink
s" id="mw-normal-catlinks"><a href="/wiki/Help:Category" title="Help:Category">Catego
ries</a>: <ul><li><a href="/wiki/Category:Lists_of_largest_private_companies_by_count
ry" title="Category:Lists of largest private companies by country">Lists of largest p
rivate companies by country</a></li><li><a href="/wiki/Category:Lists_of_companies_of
_Canada" title="Category:Lists of companies of Canada">Lists of companies of Canada</
a></li><li><a href="/wiki/Category:Economy_of_Canada" title="Category:Economy of Cana
da">Economy of Canada</a></li></ul></div><div class="mw-hidden-catlinks mw-hidden-cat
s-hidden" id="mw-hidden-catlinks">Hidden categories: <ul><li><a href="/wiki/Category:
Articles_with_short_description" title="Category:Articles with short description">Art
icles with short description</a></li><li><a href="/wiki/Category:Short_description_is
_different_from_Wikidata" title="Category:Short description is different from Wikidat
a">Short description is different from Wikidata</a></li></ul></div></div>
</div>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 38/48
</main>
</div>
<div class="mw-footer-container">
<footer class="mw-footer" id="footer" role="contentinfo">
<ul id="footer-info">
<li id="footer-info-lastmod"> This page was last edited on 4 August 2023, at 14:25<sp
an class="anonymous-show"> (UTC)</span>.</li>
<li id="footer-info-copyright">Text is available under the <a href="https://creativec
ommons.org/licenses/by-sa/4.0/" rel="license">Creative Commons Attribution-ShareAlike
License 4.0</a><a href="//creativecommons.org/licenses/by-sa/4.0/" rel="license" styl
e="display:none;"></a>;
additional terms may apply. By using this site, you agree to the <a href="//foundati
on.wikimedia.org/wiki/Terms_of_Use">Terms of Use</a> and <a href="//foundation.wikime
dia.org/wiki/Privacy_policy">Privacy Policy</a>. Wikipedia® is a registered trademark
of the <a href="//www.wikimediafoundation.org/">Wikimedia Foundation, Inc.</a>, a non
-profit organization.</li>
</ul>
<ul id="footer-places">
<li id="footer-places-privacy"><a href="https://foundation.wikimedia.org/wiki/Specia
l:MyLanguage/Policy:Privacy_policy">Privacy policy</a></li>
<li id="footer-places-about"><a href="/wiki/Wikipedia:About">About Wikipedia</a></li>
<li id="footer-places-disclaimers"><a href="/wiki/Wikipedia:General_disclaimer">Discl
aimers</a></li>
<li id="footer-places-contact"><a href="//en.wikipedia.org/wiki/Wikipedia:Contact_u
s">Contact Wikipedia</a></li>
<li id="footer-places-wm-codeofconduct"><a href="https://foundation.wikimedia.org/wik
i/Special:MyLanguage/Universal_Code_of_Conduct">Code of Conduct</a></li>
<li id="footer-places-mobileview"><a class="noprint stopMobileRedirectToggle" href
="//en.m.wikipedia.org/w/index.php?title=List_of_largest_companies_in_Canada&amp;mobi
leaction=toggle_view_mobile">Mobile view</a></li>
<li id="footer-places-developers"><a href="https://developer.wikimedia.org">Developer
s</a></li>
<li id="footer-places-statslink"><a href="https://stats.wikimedia.org/#/en.wikipedia.
org">Statistics</a></li>
<li id="footer-places-cookiestatement"><a href="https://foundation.wikimedia.org/wik
i/Special:MyLanguage/Policy:Cookie_statement">Cookie statement</a></li>
</ul>
<ul class="noprint" id="footer-icons">
<li id="footer-copyrightico"><a href="https://wikimediafoundation.org/"><img alt="Wik
imedia Foundation" height="31" loading="lazy" src="/static/images/footer/wikimedia-bu
tton.png" srcset="/static/images/footer/wikimedia-button-1.5x.png 1.5x, /static/image
s/footer/wikimedia-button-2x.png 2x" width="88"/></a></li>
<li id="footer-poweredbyico"><a href="https://www.mediawiki.org/"><img alt="Powered b
y MediaWiki" height="31" loading="lazy" src="/static/images/footer/poweredby_mediawik
i_88x31.png" srcset="/static/images/footer/poweredby_mediawiki_132x47.png 1.5x, /stat
ic/images/footer/poweredby_mediawiki_176x62.png 2x" width="88"/></a></li>
</ul>
</footer>
</div>
</div>
</div>
<div class="vector-settings" id="p-dock-bottom">
<ul>
<li><button class="cdx-button cdx-button--icon-only vector-limited-width-toggle" id
=""><span class="vector-icon mw-ui-icon-fullScreen mw-ui-icon-wikimedia-fullScreen">
</span>
<span>Toggle limited content width</span>
</button>
</li>
</ul>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 39/48
</div>
<script>(RLQ=window.RLQ||[]).push(function(){mw.config.set({"wgHostname":"mw2449","wg
BackendResponseTime":83,"wgPageParseReport":{"limitreport":{"cputime":"0.135","wallti
me":"0.182","ppvisitednodes":{"value":445,"limit":1000000},"postexpandincludesize":
{"value":3457,"limit":2097152},"templateargumentsize":{"value":298,"limit":209715
2},"expansiondepth":{"value":9,"limit":100},"expensivefunctioncount":{"value":0,"limi
t":500},"unstrip-depth":{"value":1,"limit":20},"unstrip-size":{"value":5948,"limit":5
000000},"entityaccesscount":{"value":0,"limit":400},"timingprofile":["100.00% 133.41
9 1 -total"," 59.39% 79.234 1 Template:Reflist"," 49.57% 66.142 2
Template:Cite_web"," 39.48% 52.674 1 Template:Short_description"," 21.06% 2
8.096 2 Template:Pagetype"," 8.81% 11.752 3 Template:Main_other"," 7.4
1% 9.886 1 Template:SDcat"," 3.34% 4.456 1 Template:Short_descriptio
n/lowercasecheck"," 1.55% 2.065 1 Template:First_word"]},"scribunto":{"limit
report-timeusage":{"value":"0.060","limit":"10.000"},"limitreport-memusage":{"value":
2515403,"limit":52428800}},"cachereport":{"origin":"mw2375","timestamp":"202308041425
43","ttl":1814400,"transientcontent":false}}});});</script>
<script type="application/ld+json">{"@context":"https:\/\/schema.org","@type":"Articl
e","name":"List of largest companies in Canada","url":"https:\/\/en.wikipedia.org\/wi
ki\/List_of_largest_companies_in_Canada","sameAs":"http:\/\/www.wikidata.org\/entity
\/Q1371361","mainEntity":"http:\/\/www.wikidata.org\/entity\/Q1371361","author":{"@ty
pe":"Organization","name":"Contributors to Wikimedia projects"},"publisher":{"@typ
e":"Organization","name":"Wikimedia Foundation, Inc.","logo":{"@type":"ImageObjec
t","url":"https:\/\/www.wikimedia.org\/static\/images\/wmf-hor-googpub.png"}},"datePu
blished":"2019-07-28T12:04:42Z","dateModified":"2023-08-04T14:25:15Z","headline":"Wik
imedia list article"}</script><script type="application/ld+json">{"@context":"http
s:\/\/schema.org","@type":"Article","name":"List of largest companies in Canada","ur
l":"https:\/\/en.wikipedia.org\/wiki\/List_of_largest_companies_in_Canada","sameA
s":"http:\/\/www.wikidata.org\/entity\/Q1371361","mainEntity":"http:\/\/www.wikidata.
org\/entity\/Q1371361","author":{"@type":"Organization","name":"Contributors to Wikim
edia projects"},"publisher":{"@type":"Organization","name":"Wikimedia Foundation, In
c.","logo":{"@type":"ImageObject","url":"https:\/\/www.wikimedia.org\/static\/images
\/wmf-hor-googpub.png"}},"datePublished":"2019-07-28T12:04:42Z","dateModified":"2023-
08-04T14:25:15Z","headline":"Wikimedia list article"}</script>
</body>
</html>
**Finding table in the webpage
In [40]:
#table1 = soup.find('table', class_ = 'wikitable sortable')[1]
In [50]:
table = soup.find_all('table')[0]
In [ ]:
##<table class="wikitable sortable jquery-tablesorter">
##<thead><tr>
In [51]:
print(table)
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 40/48
<table class="wikitable sortable">
<tbody><tr>
<th>Rank
</th>
<th>Fortune 500<br/>rank
</th>
<th>Name
</th>
<th>Industry
</th>
<th>Revenue<br/><small>(USD millions)</small>
</th>
<th>Profits<br/><small>(USD millions)</small>
</th>
<th>Employees
</th>
<th>Headquarters
</th></tr>
<tr>
<td>1
</td>
<td>117
</td>
<td><a class="mw-redirect" href="/wiki/Brookfield_Asset_Management" title="Brookfield
Asset Management">Brookfield Asset Management</a>
</td>
<td><a href="/wiki/Finance" title="Finance">Finance</a>
</td>
<td style="text-align:center;">92,769
</td>
<td style="text-align:center;">2,056
</td>
<td style="text-align:center;">202,500
</td>
<td><a href="/wiki/Toronto" title="Toronto">Toronto</a>
</td></tr>
<tr>
<td>2
</td>
<td>214
</td>
<td><a href="/wiki/Alimentation_Couche-Tard" title="Alimentation Couche-Tard">Aliment
ation Couche-Tard</a>
</td>
<td><a href="/wiki/Retail" title="Retail">Retail</a>
</td>
<td style="text-align:center;">62,810
</td>
<td style="text-align:center;">2,683
</td>
<td style="text-align:center;">122,000
</td>
<td><a href="/wiki/Laval,_Quebec" title="Laval, Quebec">Laval</a>
</td></tr>
<tr>
<td>3
</td>
<td>270
</td>
<td><a href="/wiki/Royal_Bank_of_Canada" title="Royal Bank of Canada">Royal Bank of C
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 41/48
anada</a>
</td>
<td><a class="mw-redirect" href="/wiki/Banking" title="Banking">Banking</a>
</td>
<td style="text-align:center;">52,062
</td>
<td style="text-align:center;">12,265
</td>
<td style="text-align:center;">91,427
</td>
<td>Toronto
</td></tr>
<tr>
<td>4
</td>
<td>277
</td>
<td><a href="/wiki/Cenovus_Energy" title="Cenovus Energy">Cenovus Energy</a>
</td>
<td><a class="mw-redirect" href="/wiki/Oil_and_Gas" title="Oil and Gas">Oil and Gas</
a>
</td>
<td style="text-align:center;">51,406
</td>
<td style="text-align:center;">4,956
</td>
<td style="text-align:center;">5,998
</td>
<td><a href="/wiki/Calgary" title="Calgary">Calgary</a>
</td></tr>
<tr>
<td>5
</td>
<td>294
</td>
<td><a href="/wiki/Toronto-Dominion_Bank" title="Toronto-Dominion Bank">Toronto-Domin
ion Bank</a>
</td>
<td>Banking
</td>
<td style="text-align:center;">48,700
</td>
<td style="text-align:center;">13,535
</td>
<td style="text-align:center;">94,945
</td>
<td>Toronto
</td></tr>
<tr>
<td>6
</td>
<td>327
</td>
<td><a href="/wiki/Suncor_Energy" title="Suncor Energy">Suncor Energy</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">44,928
</td>
<td style="text-align:center;">6,975
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 42/48
</td>
<td style="text-align:center;">16,558
</td>
<td>Calgary
</td></tr>
<tr>
<td>7
</td>
<td>336
</td>
<td><a href="/wiki/George_Weston_Limited" title="George Weston Limited">George Weston
Limited</a>
</td>
<td>Retail
</td>
<td style="text-align:center;">43,838
</td>
<td style="text-align:center;">1,396
</td>
<td style="text-align:center;">221,285
</td>
<td>Toronto
</td></tr>
<tr>
<td>8
</td>
<td>365
</td>
<td><a href="/wiki/Enbridge" title="Enbridge">Enbridge</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">40,964
</td>
<td style="text-align:center;">2,308
</td>
<td style="text-align:center;">12,050
</td>
<td>Calgary
</td></tr>
<tr>
<td>9
</td>
<td>392
</td>
<td><a href="/wiki/Nutrien" title="Nutrien">Nutrien</a>
</td>
<td><a href="/wiki/Agriculture" title="Agriculture">Agriculture</a>
</td>
<td style="text-align:center;">37,884
</td>
<td style="text-align:center;">7,660
</td>
<td style="text-align:center;">24,700
</td>
<td><a href="/wiki/Saskatoon" title="Saskatoon">Saskatoon</a>
</td></tr>
<tr>
<td>10
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 43/48
<td>394
</td>
<td><a href="/wiki/Magna_International" title="Magna International">Magna Internation
al</a>
</td>
<td><a class="mw-redirect" href="/wiki/Automotive_parts" title="Automotive parts">Aut
omotive parts</a>
</td>
<td style="text-align:center;">37,840
</td>
<td style="text-align:center;">592
</td>
<td style="text-align:center;">158,000
</td>
<td><a href="/wiki/Aurora,_Ontario" title="Aurora, Ontario">Aurora</a>
</td></tr>
<tr>
<td>11
</td>
<td>399
</td>
<td><a href="/wiki/Power_Corporation_of_Canada" title="Power Corporation of Canada">P
ower Corporation of Canada</a>
</td>
<td>Finance
</td>
<td style="text-align:center;">37,419
</td>
<td style="text-align:center;">1,510
</td>
<td style="text-align:center;">37,300
</td>
<td><a href="/wiki/Montreal" title="Montreal">Montreal</a>
</td></tr>
<tr>
<td>12
</td>
<td>415
</td>
<td><a href="/wiki/Scotiabank" title="Scotiabank">Scotiabank</a>
</td>
<td>Banking
</td>
<td style="text-align:center;">36,390
</td>
<td style="text-align:center;">7,701
</td>
<td style="text-align:center;">90,979
</td>
<td>Toronto
</td></tr>
<tr>
<td>13
</td>
<td>433
</td>
<td><a href="/wiki/Bank_of_Montreal" title="Bank of Montreal">Bank of Montreal</a>
</td>
<td>Banking
</td>
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 44/48
<td style="text-align:center;">34,730
</td>
<td style="text-align:center;">10,513
</td>
<td style="text-align:center;">46,722
</td>
<td>Montreal
</td></tr>
<tr>
<td>14
</td>
<td>471
</td>
<td><a href="/wiki/Canadian_Natural_Resources" title="Canadian Natural Resources">Can
adian Natural Resources</a>
</td>
<td>Oil and Gas
</td>
<td style="text-align:center;">32,503
</td>
<td style="text-align:center;">8,404
</td>
<td style="text-align:center;">10,035
</td>
<td>Calgary
</td></tr></tbody></table>
[<th>Rank
</th>,
<th>Fortune 500<br/>rank
</th>,
<th>Name
</th>,
<th>Industry
</th>,
<th>Revenue<br/><small>(USD millions)</small>
</th>,
<th>Profits<br/><small>(USD millions)</small>
</th>,
<th>Employees
</th>,
<th>Headquarters
</th>]
['Rank', 'Fortune 500rank', 'Name', 'Industry', 'Revenue(USD millions)', 'Profits(USD
millions)', 'Employees', 'Headquarters']
In [62]:
# viewing table title 
titles = table.find_all('th')
In [63]:
titles
Out[63]: In [ ]:
#Title for the table
In [64]:
table_title = [title.text.strip() for title in titles]
print(table_title)
In [65]: import pandas as pd
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 45/48
Rank Fortune
500rank Name Industry
Revenue(USD
millions)
Profits(USD
millions) Employees Headquarters
In [69]:
#making dataframe for the table . making titles as columns
df = pd.DataFrame(columns = table_title)
df
Out[69]: In [73]:
# pulling data from the table in the webpage 
column_data = table.find_all('tr')
In [77]:
#creating loop to get the data from the row 
for row in column_data[1:]:
 row_data = row.find_all('td')
 ind_row_data = [data.text.strip() for data in row_data]
 # print(ind_row_data)
 
 length = len(df)
 df.loc[length] = ind_row_data
In [78]:
df
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 46/48
Rank Fortune
500rank Name Industry
Revenue(USD
millions)
Profits(USD
millions) Employees Headquarters
0 1 117
Brookfield
Asset
Management
Finance 92,769 2,056 202,500 Toronto
1 2 214 Alimentation
Couche-Tard Retail 62,810 2,683 122,000 Laval
2 3 270 Royal Bank
of Canada Banking 52,062 12,265 91,427 Toronto
3 4 277 Cenovus
Energy Oil and Gas 51,406 4,956 5,998 Calgary
4 5 294
TorontoDominion
Bank
Banking 48,700 13,535 94,945 Toronto
5 6 327 Suncor
Energy Oil and Gas 44,928 6,975 16,558 Calgary
6 7 336
George
Weston
Limited
Retail 43,838 1,396 221,285 Toronto
7 8 365 Enbridge Oil and Gas 40,964 2,308 12,050 Calgary
8 9 392 Nutrien Agriculture 37,884 7,660 24,700 Saskatoon
9 10 394 Magna
International
Automotive
parts
37,840 592 158,000 Aurora
10 11 399
Power
Corporation
of Canada
Finance 37,419 1,510 37,300 Montreal
11 12 415 Scotiabank Banking 36,390 7,701 90,979 Toronto
12 13 433 Bank of
Montreal Banking 34,730 10,513 46,722 Montreal
13 14 471
Canadian
Natural
Resources
Oil and Gas 32,503 8,404 10,035 Calgary
**EDA**
Out[78]: In [ ]:
#exporting data to csv file
In [80]:
df.to_csv(r'C:\Users\1234\Desktop\Data Analysis-Projects\Webscrapping_project\canada_c
In [81]:
import matplotlib.pyplot as plt
import seaborn as sns
In [83]:
# Set the style of seaborn
sns.set(style="whitegrid")
# Plotting revenue vs. profits
plt.figure(figsize=(10, 6))
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 47/48
sns.scatterplot(x="Revenue(USD millions)", y="Profits(USD millions)", data=df, hue="In
plt.title("Revenue vs. Profits by Industry")
plt.xlabel("Revenue (USD millions)")
plt.ylabel("Profits (USD millions)")
plt.show()
In [85]:
# Convert "Revenue" column to numeric
df["Revenue(USD millions)"] = df["Revenue(USD millions)"].str.replace(",", "").astype(
In [86]:
# Plotting top industries by average revenue
plt.figure(figsize=(10, 6))
top_industries = df.groupby("Industry")["Revenue(USD millions)"].mean().sort_values(as
sns.barplot(x=top_industries.index, y=top_industries.values, palette="viridis")
plt.title("Top Industries by Average Revenue")
plt.xlabel("Industry")
plt.ylabel("Average Revenue (USD millions)")
plt.xticks(rotation=45)
plt.show()
8/4/23, 3:28 PM Webscrapping_project
file:///C:/Users/1234/Downloads/Webscrapping_project.html 48/48
In [ ]:
