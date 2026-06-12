---
title: "How to download the kdenlive manual page so I can run without wifi"
date: 2015-07-09
forum: General Help
---

### Post by Ralph L on 2015-07-09
I am running xubuntu 14.04 with kdenlive  0.9.10 (very recently installed) and khelpcenter4 installed.  The Help function doesn't work (apparently it hasn't in a long time) so the only way to access the kdenlive manual is on-line at [https://userbase.kde.org/Kdenlive/Manual](https://userbase.kde.org/Kdenlive/Manual) .  However, I often work without wifi (on airplanes, camping, etc) and would like to download the kdenlive manual page from the Internet.  I tried with the following:```
wget  \
     -e robots=off \
     --recursive \
     --page-requisites \
     --html-extension \
     --convert-links \
     --domains https://userbase.kde.org \
     --no-parent \
         https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/
```  However, I get only the index downloaded.   I can't figure out why the wget recursive function won't work.  At first I thought it was due to robot.txt, but I can find no reference to that.  Any help appreciated.....


Here is the contents of the index that gets downloaded.  It looks to me like it has links to all the sub-pages, but I don't know html.```
<!DOCTYPE html>
<html lang="en" dir="ltr" class="client-nojs">
<head>
<title>Kdenlive/Manual - KDE UserBase Wiki</title>
<meta charset="UTF-8" />
<meta name="generator" content="MediaWiki 1.20.2" />
<link rel="shortcut icon" href="https://userbase.kde.org/favicon.png" />
<link rel="search" type="application/opensearchdescription+xml" href="https://userbase.kde.org/opensearch_desc.php" title="KDE UserBase Wiki (en)" />
<link rel="EditURI" type="application/rsd+xml" href="https://userbase.kde.org/api.php?action=rsd" />
<link rel="copyright" href="https://userbase.kde.org/KDE_UserBase_Wiki:Copyrights" />
<link rel="alternate" type="application/atom+xml" title="KDE UserBase Wiki Atom feed" href="https://userbase.kde.org/index.php?title=Special:RecentChanges&amp;feed=atom" />
<link rel="stylesheet" href="https://userbase.kde.org/load.php?debug=false&amp;lang=en&amp;modules=mediawiki.legacy.commonPrint%2Cshared&amp;only=styles&amp;skin=neverland&amp;*" />
<link rel="stylesheet" href="https://cdn.kde.org/css/bootstrap.css" media="screen" />
<link rel="stylesheet" href="https://cdn.kde.org/css/bootstrap-responsive.css" media="screen" />
<link rel="stylesheet" href="https://cdn.kde.org/css/bootstrap-mediawiki.css" media="screen" /><meta name="ResourceLoaderDynamicStyles" content="" />
<link rel="stylesheet" href="https://userbase.kde.org/load.php?debug=false&amp;lang=en&amp;modules=site&amp;only=styles&amp;skin=neverland&amp;*" />
<style>a:lang(ar),a:lang(ckb),a:lang(fa),a:lang(kk-arab),a:lang(mzn),a:lang(ps),a:lang(ur){text-decoration:none}
/* cache key: userbase:resourceloader:filter:minify-css:7:e41cc55f87022af1826b3c44596536be */</style>

<script src="https://userbase.kde.org/load.php?debug=false&amp;lang=en&amp;modules=startup&amp;only=scripts&amp;skin=neverland&amp;*"></script>
<script>if(window.mw){

mw.config.set({"wgCanonicalNamespace":"","wgCanonicalSpecialPageName":false,"wgNamespaceNumber":0,"wgPageName":"Kdenlive/Manual","wgTitle":"Kdenlive/Manual","wgCurRevisionId":340521,"wgArticleId":67193,"wgIsArticle":true,"wgAction":"view","wgUserName":null,"wgUserGroups":["*"],"wgCategories":["Kdenlive","Multimedia"],"wgBreakFrames":true,"wgPageContentLanguage":"en","wgSeparatorTransformTable":["",""],"wgDigitTransformTable":["",""],"wgDefaultDateFormat":"dmy","wgMonthNames":["","January","February","March","April","May","June","July","August","September","October","November","December"],"wgMonthNamesShort":["","Jan","Feb","Mar","Apr","May","Jun","Jul","Aug","Sep","Oct","Nov","Dec"],"wgRelevantPageName":"Kdenlive/Manual","wgRestrictionEdit":[],"wgRestrictionMove":[],"wgULSLanguages":{"ab":"Abkhazian","ace":"Achinese","af":"Afrikaans","ak":"Akan","aln":"Gheg Albanian","als":"Alemannisch","am":"Amharic","an":"Aragonese","ang":"Old English","anp":"Angika","ar":"Arabic","arc":"Aramaic","arn":"Mapuche","ary":"Moroccan Spoken Arabic","arz":"Egyptian Spoken Arabic","as":"Assamese","ast":"Asturian","av":"Avaric","avk":"Kotava","ay":"Aymara","az":"Azerbaijani","ba":"Bashkir","bar":"Bavarian","bat-smg":"Samogitian","bcc":"Southern Balochi","bcl":"Bikol Central","be":"Belarusian","be-tarask":"Belarusian (Tara&#353;kievica orthography)","be-x-old":"&#8234;&#1073;&#1077;&#1083;&#1072;&#1088;&#1091;&#1089;&#1082;&#1072;&#1103; (&#1090;&#1072;&#1088;&#1072;&#1096;&#1082;&#1077;&#1074;&#1110;&#1094;&#1072;)&#8236;","bg":"Bulgarian","bh":"Bihari","bho":"Bhojpuri","bi":"Bislama","bjn":"Banjar","bm":"Bambara","bn":"Bengali","bo":"Tibetan","bpy":"Bishnupria Manipuri","bqi":"Bakhtiari","br":"Breton","brh":"Brahui","bs":"Bosnian","bug":"Buginese","ca":"Catalan","cbk-zam":"Chavacano de Zamboanga","cdo":"Min Dong Chinese","ce":"Chechen","ceb":"Cebuano","ch":"Chamorro","chr":"Cherokee","ckb":"Sorani Kurdish","co":"Corsican","cps":"Capiznon","crh":"Crimean Turkish","crh-latn":"Crimean Turkish (Latin script)","crh-cyrl":"Crimean Turkish (Cyrillic script)","cs":"Czech","csb":"Kashubian","cu":"Church Slavic","cv":"Chuvash","cy":"Welsh","da":"Danish","de":"German","de-at":"Austrian German","de-ch":"Swiss High German","de-formal":"German (formal address)","diq":"Zazaki","dsb":"Lower Sorbian","dtp":"Central Dusun","dv":"Divehi","dz":"Dzongkha","ee":"Ewe","egl":"Emiliàn","el":"Greek","eml":"Emiliano-Romagnolo","en":"English","en-ca":"Canadian English","en-gb":"British English","eo":"Esperanto","es":"Spanish","et":"Estonian","eu":"Basque","ext":"Extremaduran","fa":"Persian","ff":"Fulah","fi":"Finnish","fit":"meänkieli","fiu-vro":"Võro","fj":"Fijian","fo":"Faroese","fr":"French","frc":"Cajun French","frp":"Franco-Provençal","frr":"Northern Frisian","fur":"Friulian","fy":"Western Frisian","ga":"Irish","gag":"Gagauz","gan":"Gan","gan-hans":"Simplified Gan script","gan-hant":"Traditional Gan script","gd":"Scottish Gaelic","gl":"Galician","glk":"Gilaki","gn":"Guarani","got":"Gothic","grc":"Ancient Greek","gsw":"Swiss German","gu":"Gujarati","gv":"Manx","ha":"Hausa","hak":"Hakka","haw":"Hawaiian","he":"Hebrew","hi":"Hindi","hif":"Fiji Hindi","hif-latn":"Fiji Hindi (Latin script)","hil":"Hiligaynon","hr":"Croatian","hsb":"Upper Sorbian","ht":"Haitian","hu":"Hungarian","hy":"Armenian","ia":"Interlingua","id":"Indonesian","ie":"Interlingue","ig":"Igbo","ii":"Sichuan Yi","ik":"Inupiaq","ike-cans":"Eastern Canadian (Aboriginal syllabics)","ike-latn":"Eastern Canadian (Latin script)","ilo":"Iloko","inh":"Ingush","io":"Ido","is":"Icelandic","it":"Italian","iu":"Inuktitut","ja":"Japanese","jam":"Jamaican Creole English","jbo":"Lojban","jut":"Jutish","jv":"Javanese","ka":"Georgian","kaa":"Kara-Kalpak","kab":"Kabyle","kbd":"Kabardian","kbd-cyrl":"&#1040;&#1076;&#1099;&#1075;&#1101;&#1073;&#1079;&#1101;","kg":"Kongo","khw":"Khowar","kiu":"Kirmanjki","kk":"Kazakh","kk-arab":"Kazakh (Arabic script)","kk-cyrl":"Kazakh (Cyrillic script)","kk-latn":"Kazakh (Latin script)","kk-cn":"Kazakh (China)","kk-kz":"Kazakh (Kazakhstan)","kk-tr":"Kazakh (Turkey)","kl":"Kalaallisut","km":"Khmer","kn":"Kannada","ko":"Korean","ko-kp":"&#54620;&#44397;&#50612; (&#51312;&#49440;)","koi":"Komi-Permyak","krc":"Karachay-Balkar","kri":"Krio","krj":"Kinaray-a","ks":"Kashmiri","ks-arab":"Kashmiri (Arabic script)","ks-deva":"Kashmiri (Devanagari script)","ksh":"Colognian","ku":"Kurdish","ku-latn":"Kurdish (Latin script)","ku-arab":"&#8235;&#1603;&#1608;&#1585;&#1583;&#1610; (&#1593;&#1749;&#1585;&#1749;&#1576;&#1740;)&#8236;","kv":"Komi","kw":"Cornish","ky":"Kirghiz","la":"Latin","lad":"Ladino","lb":"Luxembourgish","lbe":"&#1083;&#1072;&#1082;&#1082;&#1091;","lez":"Lezghian","lfn":"Lingua Franca Nova","lg":"Ganda","li":"Limburgish","lij":"Ligure","liv":"L&#299;võ k&#275;&#316;","lmo":"lumbaart","ln":"Lingala","lo":"Lao","loz":"Lozi","lt":"Lithuanian","ltg":"Latgalian","lus":"Mizo","lv":"Latvian","lzh":"Literary Chinese","lzz":"Lazuri","mai":"Maithili","map-bms":"Basa Banyumasan","mdf":"Moksha","mg":"Malagasy","mhr":"Eastern Mari","mi":"Maori","min":"Minangkabau","mk":"Macedonian","ml":"Malayalam","mn":"Mongolian","mo":"Moldavian","mr":"Marathi","mrj":"Hill Mari","ms":"Malay","mt":"Maltese","mwl":"Mirandese","my":"Burmese","myv":"Erzya","mzn":"Mazanderani","na":"Nauru","nah":"Nahuatl","nan":"Min Nan Chinese","nap":"Neapolitan","nb":"Norwegian Bokmål","nds":"Low German","nds-nl":"Nedersaksisch","ne":"Nepali","new":"Newari","niu":"Niuean","nl":"Dutch","nl-informal":"&#8234;Nederlands (informeel)&#8236;","nn":"Norwegian Nynorsk","no":"Norwegian (bokmål)","nov":"Novial","nso":"Northern Sotho","nv":"Navajo","ny":"Nyanja","oc":"Occitan","om":"Oromo","or":"Oriya","os":"Ossetic","pa":"Punjabi","pag":"Pangasinan","pam":"Pampanga","pap":"Papiamento","pcd":"Picard","pdc":"Deitsch","pdt":"Plautdietsch","pfl":"Pälzisch","pi":"Pali","pih":"Norfuk / Pitkern","pl":"Polish","pms":"Piedmontese","pnb":"Western Punjabi","pnt":"Pontic","prg":"Prussian","ps":"Pashto","pt":"Portuguese","pt-br":"Brazilian Portuguese","qu":"Quechua","qug":"Runa shimi","rgn":"Romagnol","rif":"Tarifit","rm":"Romansh","rmy":"Romani","ro":"Romanian","roa-rup":"Aromanian","roa-tara":"tarandíne","ru":"Russian","rue":"Rusyn","rup":"Aromanian","ruq":"Megleno-Romanian","ruq-cyrl":"Megleno-Romanian (Cyrillic script)","ruq-latn":"Megleno-Romanian (Latin script)","sa":"Sanskrit","sah":"Sakha","sat":"Santali","sc":"Sardinian","scn":"Sicilian","sco":"Scots","sd":"Sindhi","sdc":"Sassaresu","se":"Northern Sami","sei":"Cmique Itom","sg":"Sango","sgs":"Samogitian","sh":"Serbo-Croatian","shi":"Tachelhit","si":"Sinhala","simple":"Simple English","sk":"Slovak","sl":"Slovenian","sli":"Lower Silesian","sm":"Samoan","sma":"Southern Sami","sn":"Shona","so":"Somali","sq":"Albanian","sr":"Serbian","sr-ec":"Serbian (Cyrillic script)","sr-el":"Serbian (Latin script)","srn":"Sranan Tongo","ss":"Swati","st":"Southern Sotho","stq":"Seeltersk","su":"Sundanese","sv":"Swedish","sw":"Swahili","szl":"Silesian","ta":"Tamil","tcy":"Tulu","te":"Telugu","tet":"Tetum","tg":"Tajik","tg-cyrl":"Tajik (Cyrillic script)","tg-latn":"Tajik (Latin script)","th":"Thai","ti":"Tigrinya","tk":"Turkmen","tl":"Tagalog","tly":"&#1090;&#1086;&#1083;&#1099;&#1096;&#1241; &#1079;&#1099;&#1074;&#1086;&#1085;","tn":"Tswana","to":"Tongan","tokipona":"Toki Pona","tpi":"Tok Pisin","tr":"Turkish","tru":"Turoyo","ts":"Tsonga","tt":"Tatar","tt-cyrl":"Tatar (Cyrillic script)","tt-latn":"Tatar (Latin script)","ty":"Tahitian","tyv":"Tuvinian","udm":"Udmurt","ug":"Uighur","ug-arab":"Uyghur (Arabic script)","ug-latn":"Uyghur (Latin script)","uk":"Ukrainian","ur":"Urdu","uz":"Uzbek","ve":"Venda","vec":"vèneto","vep":"Veps","vi":"Vietnamese","vls":"West-Vlams","vmf":"Upper Franconian","vo":"Volapük","vot":"Votic","vro":"Võro","wa":"Walloon","war":"Waray","wo":"Wolof","wuu":"Wu","xal":"Kalmyk","xh":"Xhosa","xmf":"Mingrelian","yi":"Yiddish","yo":"Yoruba","yue":"Cantonese","za":"Zhuang","zea":"Zeeuws","zh":"Chinese","zh-classical":"Classical Chinese","zh-cn":"Chinese (China)","zh-hans":"Simplified Chinese","zh-hant":"Traditional Chinese","zh-hk":"Chinese (Hong Kong)","zh-min-nan":"Chinese (Min Nan)","zh-mo":"&#8234;&#20013;&#25991;&#65288;&#28595;&#38272;&#65289;&#8236;","zh-my":"&#8234;&#20013;&#25991;&#65288;&#39532;&#26469;&#35199;&#20122;&#65289;&#8236;","zh-sg":"Chinese (Singapore)","zh-tw":"Chinese (Taiwan)","zh-yue":"Cantonese","zu":"Zulu"},"wgULSAcceptLanguageList":[],"egMapsDebugJS":false,"wgWikiEditorEnabledModules":{"toolbar":false,"dialogs":false,"hidesig":true,"templateEditor":false,"templates":false,"preview":false,"previewDialog":false,"publish":false,"toc":false}});
}</script><script>if(window.mw){
mw.loader.implement("user.options",function(){mw.user.options.set({"ccmeonemails":0,"cols":80,"date":"default","diffonly":0,"disablemail":0,"disablesuggest":0,"editfont":"default","editondblclick":0,"editsection":true,"editsectiononrightclick":0,"enotifminoredits":0,"enotifrevealaddr":0,"enotifusertalkpages":1,"enotifwatchlistpages":0,"extendwatchlist":0,"externaldiff":0,"externaleditor":0,"fancysig":0,"forceeditsummary":0,"gender":"unknown","hideminor":0,"hidepatrolled":0,"imagesize":2,"justify":0,"math":1,"minordefault":0,"newpageshidepatrolled":0,"nocache":0,"noconvertlink":0,"norollbackdiff":0,"numberheadings":0,"previewonfirst":0,"previewontop":1,"quickbar":5,"rcdays":7,"rclimit":100,"rememberpassword":0,"rows":25,"searchlimit":20,"showhiddencats":0,"showjumplinks":1,"shownumberswatching":1,"showtoc":1,"showtoolbar":1,"skin":"neverland","stubthreshold":0,"thumbsize":2,"underline":2,"uselivepreview":0,"usenewrc":1,"watchcreations":0,"watchdefault":0,"watchdeletion":0,
"watchlistdays":3,"watchlisthideanons":0,"watchlisthidebots":0,"watchlisthideliu":0,"watchlisthideminor":0,"watchlisthideown":0,"watchlisthidepatrolled":0,"watchmoves":0,"wllimit":250,"translate":0,"translate-editlangs":"default","translate-jsedit":1,"translate-recent-groups":"","lqtnotifytalk":false,"lqtdisplaydepth":5,"lqtdisplaycount":25,"lqtcustomsignatures":true,"lqt-watch-threads":true,"openid-hide":0,"openid-update-on-login-nickname":false,"openid-update-on-login-email":false,"openid-update-on-login-fullname":false,"openid-update-on-login-language":false,"openid-update-on-login-timezone":false,"variant":"en","language":"en","searchNs0":true,"searchNs1":false,"searchNs2":false,"searchNs3":false,"searchNs4":false,"searchNs5":false,"searchNs6":false,"searchNs7":false,"searchNs8":false,"searchNs9":false,"searchNs10":false,"searchNs11":false,"searchNs12":false,"searchNs13":false,"searchNs14":false,"searchNs15":false,"searchNs90":false,"searchNs91":false,"searchNs92":false,
"searchNs93":false,"searchNs400":false,"searchNs401":false,"searchNs402":false,"searchNs403":false,"searchNs420":false,"searchNs421":false,"searchNs1198":false,"searchNs1199":false});;},{},{});mw.loader.implement("user.tokens",function(){mw.user.tokens.set({"editToken":"+\\","watchToken":false});;},{},{});
/* cache key: userbase:resourceloader:filter:minify-js:7:d62787a9d3edfdb314877f45a3a4d931 */
}</script>
<script>if(window.mw){
mw.loader.load(["ext.translate","mediawiki.page.startup","mediawiki.legacy.wikibits","mediawiki.legacy.ajax","ext.uls.init"]);
}</script>
		<style type='text/css'>
		li#pt-openidlogin {
		  background: url(https://userbase.kde.org/extensions/OpenID/skin/icons/openid-inputicon.png) top left no-repeat;
		  padding-left: 20px;
		  text-transform: none;
		}
		</style>
</head>
<body class="mediawiki ltr sitedir-ltr ns-0 ns-subject page-Kdenlive_Manual skin-neverland action-view">

	<!-- header -->
	<div id="top-small mw-head" class="navbar navbar-static-top Neverland noprint">
		<div class="navbar-inner">
			<div class="container">
				<div class="pull-right">
					
<!-- 0 -->
					<div id="p-search">
						<form action="https://userbase.kde.org/index.php" id="searchform" class="form-inline">
							<input id="searchInput" name="search" type="search" placeholder="Search"
								   class="input-large" autocomplete="off"
															value=""
							 />

							<input type="hidden" name="title" value="Special:Search" />
						</form>
					</div>
				
<!-- /0 -->
				</div>

				<a href="https://userbase.kde.org/Welcome_to_KDE_UserBase" class="brand">
					<img src="https://cdn.kde.org/img/logo.plain.small.png" alt="" />
					KDE UserBase Wiki				</a>
			</div>
		</div>
	</div>
	<!-- /header -->
	
	<div id="top" class="container">
		<!-- content -->
		<div class="row">
			<div class="span9">
				<div>
					<div id="mw-js-message" class="alert alert-info" style="display:none;"
						>
					</div>

					
					<!-- page-actions -->
					
<!-- 0 -->
					<div class="btn-group pull-right page-actions"> <!-- Is closed later in the 'actions' section -->
																	<a href="index.html" class="btn btn-mini
																	btn-primary
								"
								>

																	<i class="icon-ca-view																							icon-white
											"></i>
									View															</a>
													<a href="https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;action=edit" class="btn btn-mini
								"
								 title="This page is protected.
You can view its source [e]" accesskey="e">

																	<i class="icon-ca-viewsource																							icon-black
											"></i>
									View source															</a>
													<a href="https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;action=history" class="btn btn-mini
								"
								 title="Past revisions of this page [h]" accesskey="h">

																	<i class="icon-ca-history																							icon-black
											"></i>
									History															</a>
											
<!-- /0 -->

<!-- 1 -->
					</div> <!-- Opened in the 'views' section -->
				
<!-- /1 -->
					<!-- /page-actions -->

					<!-- top-navigation -->
					
<!-- 0 -->
						<ul class="nav nav-tabs">
															<li class="active">
									<a href="index.html#"  title="View the content page [c]" accesskey="c">
										Page									</a>
								</li>
																<li>
										<a href="https://userbase.kde.org/Talk:Kdenlive/Manual"  title="Discussion about the content page [t]" accesskey="t">
										Discussion										</a>
									</li>
													</ul>
					
<!-- /0 -->
					<!-- /top-navigation -->

					<!-- firstHeading -->
					<h1 id="firstHeading">
						Kdenlive/Manual					</h1>
					<!-- /firstHeading -->

					<!-- bodyContent -->
					<div id="bodyContent">
						<!-- subtitle -->
						<div id="contentSub"><span class="subpages"><a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive" title="Special:MyLanguage/Kdenlive">Kdenlive</a></span></div>
						<!-- /subtitle -->

						
						
													<!-- jumpto -->
							<div id="jump-to-nav" class="mw-jump">
								Jump to: <a href="index.html#mw-head">navigation</a>,
								<a href="index.html#p-search">search</a>
							</div>
							<!-- /jumpto -->
						
						<!-- bodycontent -->
						<div id="mw-content-text" lang="en" dir="ltr" class="mw-content-ltr"><div class="mw-pt-languages noprint" lang="en" dir="ltr"><table><tbody><tr valign="top"><td class="mw-pt-languages-label">Other languages:</td><td class="mw-pt-languages-list"><a href="https://userbase.kde.org/Kdenlive/Manual/da" title="Kdenlive/Manual/da">Danish</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-5.png" alt="100%" title="100%" width="9" height="9" />*&#8226;*&#8206;<span class="mw-pt-languages-ui mw-pt-languages-selected">English</span> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-5.png" alt="100%" title="100%" width="9" height="9" />*&#8226;*&#8206;<a href="https://userbase.kde.org/Kdenlive/Manual/fr" title="Kdenlive/Manual/fr">French</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-4.png" alt="64%" title="64%" width="9" height="9" />*&#8226;*&#8206;<a href="https://userbase.kde.org/Kdenlive/Manual/ru" title="Kdenlive/Manual/ru">Russian</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-5.png" alt="100%" title="100%" width="9" height="9" />*&#8226;*&#8206;<a href="https://userbase.kde.org/Kdenlive/Manual/tr" title="Kdenlive/Manual/tr">Turkish</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-1.png" alt="8%" title="8%" width="9" height="9" />*&#8226;*&#8206;<a href="https://userbase.kde.org/Kdenlive/Manual/uk" title="Kdenlive/Manual/uk">Ukrainian</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-5.png" alt="100%" title="100%" width="9" height="9" />*&#8226;*&#8206;<a href="https://userbase.kde.org/Kdenlive/Manual/zh-tw" title="Kdenlive/Manual/zh-tw">Chinese (Taiwan)</a> <img src="https://userbase.kde.org/extensions/Translate/resources/images/prog-5.png" alt="94%" title="94%" width="9" height="9" /></td></tr></tbody></table></div>
<div class="manualtoc">
<h2> <span class="mw-headline" id="Table_of_Contents"> Table of Contents </span></h2>
<ol><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Introduction" title="Special:MyLanguage/Kdenlive/Manual/Introduction">Introduction</a>
</li><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Installation" title="Special:MyLanguage/Kdenlive/Manual/Installation">Installation</a>
</li><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/QuickStart" title="Special:MyLanguage/Kdenlive/Manual/QuickStart">Quick Start</a>
</li><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Tutorials" title="Special:MyLanguage/Kdenlive/Manual/Tutorials">Tutorials</a>
</li><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files">Project and File management</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Project_Tree" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Project Tree">The Project Tree</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Project" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Project">Project File Details</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Project_Settings" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Project Settings">Settings</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Notes" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Notes">Annotating</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Archiving" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Archiving">Archiving</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Backup" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Backup">Backup</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Clips" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Clips">Clips</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Importing" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Importing">Importing</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Projects_and_Files/Management" title="Special:MyLanguage/Kdenlive/Manual/Projects and Files/Management">Management</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline" title="Special:MyLanguage/Kdenlive/Manual/Timeline">Timeline</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline/Editing" title="Special:MyLanguage/Kdenlive/Manual/Timeline/Editing">Editing</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline/Grouping" title="Special:MyLanguage/Kdenlive/Manual/Timeline/Grouping">Grouping</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline/Guides" title="Special:MyLanguage/Kdenlive/Manual/Timeline/Guides">Guides</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline/Right_Click_Menu" title="Special:MyLanguage/Kdenlive/Manual/Timeline/Right Click Menu">Right Click Menu</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects_And_Transitions" title="Special:MyLanguage/Kdenlive/Manual/Effects And Transitions">Alphabetical List of Effects and Transitions</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Transitions" title="Special:MyLanguage/Kdenlive/Manual/Transitions">Transitions</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects" title="Special:MyLanguage/Kdenlive/Manual/Effects">Effects</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Alpha_manipulation" title="Special:MyLanguage/Kdenlive/Manual/Effects/Alpha manipulation">Alpha manipulation</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Audio" title="Special:MyLanguage/Kdenlive/Manual/Effects/Audio">Audio</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Audio_channels" title="Special:MyLanguage/Kdenlive/Manual/Effects/Audio channels">Audio channels</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Audio_Correction" title="Special:MyLanguage/Kdenlive/Manual/Effects/Audio Correction">Audio Correction</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Blur_and_hide" title="Special:MyLanguage/Kdenlive/Manual/Effects/Blur and hide">Blur and hide</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Colour" title="Special:MyLanguage/Kdenlive/Manual/Effects/Colour">Colour</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Colour_Correction" title="Special:MyLanguage/Kdenlive/Manual/Effects/Colour Correction">Colour Correction</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Crop_and_transform" title="Special:MyLanguage/Kdenlive/Manual/Effects/Crop and transform">Crop and transform</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Custom" title="Special:MyLanguage/Kdenlive/Manual/Effects/Custom">Custom</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Distort" title="Special:MyLanguage/Kdenlive/Manual/Effects/Distort">Distort</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Enhancement" title="Special:MyLanguage/Kdenlive/Manual/Effects/Enhancement">Enhancement</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Fade" title="Special:MyLanguage/Kdenlive/Manual/Effects/Fade">Fade</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Fun" title="Special:MyLanguage/Kdenlive/Manual/Effects/Fun">Fun</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Misc" title="Special:MyLanguage/Kdenlive/Manual/Effects/Misc">Misc</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Effects/Motion" title="Special:MyLanguage/Kdenlive/Manual/Effects/Motion">Motion</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Titles" title="Special:MyLanguage/Kdenlive/Manual/Titles">Titles</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Monitors" title="Special:MyLanguage/Kdenlive/Manual/Monitors">Monitors</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Menu" title="Special:MyLanguage/Kdenlive/Manual/Menu">Menu</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/File_Menu" title="Special:MyLanguage/Kdenlive/Manual/File Menu">File Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Edit_Menu" title="Special:MyLanguage/Kdenlive/Manual/Edit Menu">Edit Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Project_Menu" title="Special:MyLanguage/Kdenlive/Manual/Project Menu">Project Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline/Tool_Menu" title="Special:MyLanguage/Kdenlive/Manual/Timeline/Tool Menu">Tool Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Clip_Menu" title="Special:MyLanguage/Kdenlive/Manual/Clip Menu">Clip Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Timeline_Menu" title="Special:MyLanguage/Kdenlive/Manual/Timeline Menu">Timeline Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Monitor_Menu" title="Special:MyLanguage/Kdenlive/Manual/Monitor Menu">Monitor Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/View_Menu" title="Special:MyLanguage/Kdenlive/Manual/View Menu">View Menu</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Settings_Menu" title="Special:MyLanguage/Kdenlive/Manual/Settings Menu">Settings Menu</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Project_Menu/Render" title="Special:MyLanguage/Kdenlive/Manual/Project Menu/Render">Render</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Rendering" title="Special:MyLanguage/Kdenlive/Manual/Rendering">Rendering using guides and scripts</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Project_Menu/Render/Render_Profile_Parameters" title="Special:MyLanguage/Kdenlive/Manual/Project Menu/Render/Render Profile Parameters">Render Profile Parameters</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Capturing" title="Special:MyLanguage/Kdenlive/Manual/Capturing">Capturing Video</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/CapturingAudio" title="Special:MyLanguage/Kdenlive/Manual/CapturingAudio">Capturing Audio</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Toolbars" title="Special:MyLanguage/Kdenlive/Manual/Toolbars">Toolbars</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/ShootingHints" title="Special:MyLanguage/Kdenlive/Manual/ShootingHints">Shooting Hints</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Troubleshooting_and_Common_Problems" title="Special:MyLanguage/Kdenlive/Manual/Troubleshooting and Common Problems">Troubleshooting and Common Problems</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms" title="Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms">Kdenlive on other Desktops and Operating Systems</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms/Non-KDE_Desktops" title="Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms/Non-KDE Desktops">Non-KDE Desktops</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms/OSX" title="Special:MyLanguage/Kdenlive/Manual/KdenliveOnOtherPlatforms/OSX">Kdenlive on OS X</a>
</li></ol>
</li><li>  <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information" title="Special:MyLanguage/Kdenlive/Manual/Useful Information">Useful Information</a>
<ol><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/FAQ" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/FAQ">FAQ</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/VersionHistory" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/VersionHistory">Version History</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/Shortcuts" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/Shortcuts">Shortcuts</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/Surround_Sound" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/Surround Sound">Surround Sound</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/Tips_Tricks" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/Tips Tricks">Tips &amp; Tricks</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Useful_Information/Useful_Resources" title="Special:MyLanguage/Kdenlive/Manual/Useful Information/Useful Resources">Useful Resources</a>
</li></ol>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/BugReporting" title="Special:MyLanguage/Kdenlive/Manual/BugReporting">Bug Reporting</a>
</li><li> <a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Credits_and_License" title="Special:MyLanguage/Kdenlive/Manual/Credits and License">Credits and License</a>
</li></ol>
</div>
<ul class="pager">
<li><a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive" title="Special:MyLanguage/Kdenlive">&#8592; Main Page</a></li>
<li><b><strong class="selflink">&#8593; Contents page &#8593;</strong></b></li>
<li><a href="https://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/Introduction" title="Special:MyLanguage/Kdenlive/Manual/Introduction">Introduction &#8594;</a></li>
</ul>

<!-- 
NewPP limit report
Preprocessor visited node count: 40/1000000
Preprocessor generated node count: 253/1000000
Post-expand include size: 407/2097152 bytes
Template argument size: 212/2097152 bytes
Highest expansion depth: 3/40
Expensive parser function count: 0/100
-->

<!-- Saved in parser cache with key userbase:pcache:idhash:67193-0!*!*!*!en!*!* and timestamp 20150709202229 -->
</div>						<!-- /bodycontent -->

													<!-- printfooter -->
							<div class="printfooter">
								Retrieved from "<a href="https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;oldid=340521">https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;oldid=340521</a>"							</div>
						<!-- /printfooter -->
						
													<!-- catlinks -->
							<div id='catlinks' class='catlinks'><div id="mw-normal-catlinks" class="mw-normal-catlinks"><a href="https://userbase.kde.org/Special:Categories" title="Special:Categories">Categories</a>: <ul><li><a href="https://userbase.kde.org/Category:Kdenlive" title="Category:Kdenlive">Kdenlive</a></li><li><a href="https://userbase.kde.org/Category:Multimedia" title="Category:Multimedia">Multimedia</a></li></ul></div></div>							<!-- /catlinks -->
						
						
						<div class="visualClear"></div>

						<!-- debughtml -->
												<!-- /debughtml -->

						<!-- pagestats -->
																<br />
										<div class="page-info">
																							 This page was last modified on 12 December 2014, at 14:17.																							This page has been accessed 109,963 times.																							Content is available under <a class="external" href="https://userbase.kde.org/KDE_UserBase_Wiki:Copyrights">Creative Commons License SA 3.0 and the GNU Free Documentation License 1.2</a>.																					</div>
															<!-- /pagestats -->
					</div>
					<!-- /bodyContent -->
				</div>
				</div>

				<!-- panel -->
				<div class="span3 sidebar noprint" valign="top">
					<div class="well">
						<ul class="unstyled">
							<!-- logo -->
								<img src="https://userbase.kde.org/skins/neverland/images/sidebar-logo.png" alt="" />
							<!-- /logo -->

							
<!-- 0 -->

<!-- /0 -->

<!-- Navigation -->
			<li class="list-header" id='p-Navigation' >
				Navigation			</li>
		<li id="n-ub-home"><a href="https://userbase.kde.org/Special:MyLanguage/Welcome_to_KDE_UserBase">Home</a></li><li id="n-ub-start-contributing"><a href="https://userbase.kde.org/Special:MyLanguage/Quick_Start">Quick Start</a></li><li id="n-recentchanges"><a href="https://userbase.kde.org/Special:RecentChanges" title="A list of recent changes in the wiki [r]" accesskey="r">Recent changes</a></li>
<!-- /Navigation -->

<!-- ub-contributors -->
			<li class="list-header" id='p-ub-contributors' >
				Contributors			</li>
		<li id="n-ub-helpfiles"><a href="https://userbase.kde.org/Special:MyLanguage/Tasks_and_Tools">Start Contributing</a></li><li id="n-ub-helpfiles-modify"><a href="https://userbase.kde.org/Ub-helpfiles-modify-redirect">Modify Existing Pages</a></li><li id="n-ub-helpfiles-new-content"><a href="https://userbase.kde.org/Ub-helpfiles-new-content-redirect">Add New Pages</a></li><li id="n-ub-helpfiles-page-elements"><a href="https://userbase.kde.org/Special:MyLanguage/PageLayout">Page Elements Explained</a></li><li id="n-ub-helpfiles-typographical-guidelines"><a href="https://userbase.kde.org/Special:MyLanguage/Typographical_Guidelines">Display elements markup</a></li><li id="n-ub-helpfiles-markup"><a href="https://userbase.kde.org/Special:MyLanguage/Toolbox">More Markup Help</a></li>
<!-- /ub-contributors -->

<!-- ub-translators -->
			<li class="list-header" id='p-ub-translators' >
				Translators			</li>
		<li id="n-ub-get-trans-account"><a href="https://userbase.kde.org/Special:MyLanguage/Translator_Account">Get a Translator Account</a></li><li id="n-ub-languages-represented"><a href="https://userbase.kde.org/Special:MyLanguage/Special:SupportedLanguages">Languages represented</a></li><li id="n-ub-helpfiles-languages"><a href="https://userbase.kde.org/Ub-helpfiles-languages-redirect">Working with Languages</a></li><li id="n-ub-trans-tool"><a href="https://userbase.kde.org/Special:MyLanguage/Special:LanguageStats">Start Translating</a></li><li id="n-ub-release-request"><a href="https://userbase.kde.org/ReadyForTranslation">Request Release</a></li>
<!-- /ub-translators -->

<!-- SEARCH -->

<!-- /SEARCH -->

<!-- TOOLBOX -->
			<li class="list-header" id='p-tb' >
				Toolbox			</li>
		<li id="t-whatlinkshere"><a href="https://userbase.kde.org/Special:WhatLinksHere/Kdenlive/Manual" title="A list of all wiki pages that link here [j]" accesskey="j">What links here</a></li><li id="t-recentchangeslinked"><a href="https://userbase.kde.org/Special:RecentChangesLinked/Kdenlive/Manual" title="Recent changes in pages linked from this page [k]" accesskey="k">Related changes</a></li><li id="t-specialpages"><a href="https://userbase.kde.org/Special:SpecialPages" title="A list of all special pages [q]" accesskey="q">Special pages</a></li><li id="t-print"><a href="https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;printable=yes" rel="alternate" title="Printable version of this page [p]" accesskey="p">Printable version</a></li><li id="t-permalink"><a href="https://userbase.kde.org/index.php?title=Kdenlive/Manual&amp;oldid=340521" title="Permanent link to this revision of the page">Permanent link</a></li>
<!-- /TOOLBOX -->

<!-- LANGUAGES -->

<!-- /LANGUAGES -->

<!-- 0 -->
						<li class="list-header">
							Personal tools						</li>

													<li id="pt-uls" class="active"><a href="index.html#" class="uls-trigger">English</a></li>													<li id="pt-login"><a href="https://userbase.kde.org/index.php?title=Special:UserLogin&amp;returnto=Kdenlive%2FManual" title="You are encouraged to log in; however, it is not mandatory [o]" accesskey="o">Log in</a></li>													<li id="pt-openidlogin"><a href="https://userbase.kde.org/index.php?title=Special:OpenIDLogin&amp;returnto=Kdenlive/Manual">OpenID / Identity login</a></li>											
<!-- /0 -->
						</ul>
					</div>
				</div>
				<!-- /panel -->
			</div>

		<!-- /content -->

		<!-- footer -->
		<div id="footerRow">
			<div class="navbar navbar-bottom Neverland" >
				<div class="navbar-inner">
					<div class="container">
																<ul id="footer-places" class="nav">
																							<li>
													<i class="icon-privacy icon-white"></i>
													<a href="https://userbase.kde.org/KDE_UserBase_Wiki:Privacy_policy" title="KDE UserBase Wiki:Privacy policy">Privacy policy</a>												</li>
																							<li>
													<i class="icon-about icon-white"></i>
													<a href="https://userbase.kde.org/KDE_UserBase_Wiki:About" title="KDE UserBase Wiki:About">About KDE UserBase Wiki</a>												</li>
																							<li>
													<i class="icon-disclaimer icon-white"></i>
													<a href="https://userbase.kde.org/KDE_UserBase_Wiki:General_disclaimer" title="KDE UserBase Wiki:General disclaimer">Disclaimers</a>												</li>
																					</ul>
									
						<ul class="nav pull-right">
							<li id="global-nav-links" class="dropdown dropdown-hover">
								<a href="index.html#" class="dropdown-toggle" data-toggle="dropdown" data-target="#global-nav-links">
									<i class="icon-list icon-white"></i>
									KDE Links
									<b class="caret-up"></b>
								</a>

								<ul id="global-nav" class="dropdown-menu bottom-up"></ul>
							</li>
						</ul>
					</div>
				</div>
			</div>

			<footer class="Neverland">
				KDE<sup>®</sup> and the K Desktop Environment<sup>®</sup> logo are registered trademarks of <a href="http://ev.kde.org/" title="Homepage of the KDE non-profit Organization">KDE e.V.</a> &bull; <a href="http://www.kde.org/contact/impressum.php">Legal</a>			</footer>
		</div>
		<!-- /footer -->

		<script>if(window.mw){
mw.loader.state({"site":"loading","user":"missing","user.groups":"ready"});
}</script>
<script>if(window.mw){
mw.loader.load(["mediawiki.user","mediawiki.page.ready","mediawiki.searchSuggest","ext.uls.geoclient"], null, true);
}</script>
<script src="https://userbase.kde.org/load.php?debug=false&amp;lang=en&amp;modules=site&amp;only=scripts&amp;skin=neverland&amp;*"></script>
<!-- Served in 0.156 secs. -->
		<script type="text/javascript" src="https://cdn.kde.org/js/bootstrap.js"></script>
		<script type="text/javascript" src="https://cdn.kde.org/js/bootstrap-neverland.js"></script>
		<script type="text/javascript" src="https://cdn.kde.org/nav/global-nav.js"></script>
	</body>
</html>


```

---

### Post by Portaro on 2015-07-09
Maybe the wiki and printable version is not finished and because this you only have the Index file.

---

### Post by Ralph L on 2015-07-10
Portaro:  Thanks for the response.  I appreciate it.  The kdenlive manual IS available at [https://userbase.kde.org/Kdenlive/Manual](https://userbase.kde.org/Kdenlive/Manual) .  It is complete and very readable.  My problem is that I need to work offline, so I need to download the manual to my computer.  As I discussed in my original post I tried to use the recursive feature of wget to do the download.  I have used this method before to download the manual for Geeqie, and it worked very well.  However, for some reason recursive wget won't work with the kdenlive manual.  That is for what I am seeking help.......  I would very much appreciate any other thoughts on how to get the recursive feature of wget to work on the kdenlive manual.

---

### Post by Keith_Helms on 2015-07-11
Try changing the command to --domains=userbase.kde.org  That got the download going for me.  I also removed --no-parent, but I'm not sure if that mattered. 

Be aware that this site may be a bit too tricky for wget to handle.  I've let the download run for nearly an hour.  So far, it's pulled down over 8000 files and is still going.  I still can't open any links off the index page without getting "File Not Found", so I'm not confident this is going to work.

---

### Post by Ralph L on 2015-07-21
Through a lot of trial and error I finally got the kdenlive manual (mostly) downloaded so that I can use it off-line with no wifi.  From my point of view it would be nice if somebody on the kdenlive project would create a .pdf file of it, but short of that the following seems to work to download it.  Note that wget downloads to your current directory so you need to create an empty directory and "cd" to it, before running wget.```
wget  \
    --verbose \
     --progress=bar \
     -e robots=off \
     --recursive \
     --page-requisites \
     --html-extension \
     --convert-links \
     --domains=userbase.kde.org,www.youtube.com \
     --include-directories=/Special:MyLanguage/,/Kdenlive/,/Manual/,images.userbase/ \
         http://userbase.kde.org/Special:MyLanguage/Kdenlive/Manual/
```
The first 3 options listed didn't seem to do anything, but I left them in, because they were in, when I did the download.  To launch the kdenlive manual in firefox, go to folder_containing_download/userbase.kde.org/Special:MyLanguage/Kdenlive/Manual.1.html and double click it.  I created a symbolic link to it and put the link in a handy spot.
Some links off to various web-sites, not part of kdenlive documentation, didn't work, but evey link within the kdenlive documentation seemed to work.
Thanks to everybody that helped me, particularly Keith_Helms

---

