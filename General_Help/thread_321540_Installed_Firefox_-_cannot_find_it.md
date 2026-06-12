---
title: "Installed Firefox - cannot find it"
date: 2006-12-19
forum: General Help
---

### Post by samden on 2006-12-19
I am running Xubuntu dapper on an iMac G3. I have been setting it up for my use, and I think I did something funny in the Firefox settings that caused it to crash. In the end it was crashing as soon as it started to open, before it even appeared on screen, so I decided to reinstall it using Synaptic. According to Synaptic the installation was fine (I have repeated it a few times to be sure).

However, when I reinstalled it I could not open it at all. The web browser button in the toolbar no longer opens it - just gives a message:

Could not run "Web browser"
Failed to execute child process "firefox" (No such file or directory)

I have tried installing version 2.0 - no go there at all, doesn't seem to want to install. So am sticking to version 1.5 for now. I am posting this from Mozilla browser, which would install, but is a bit more clunky than Firefox - I would prefer to be using Firefox.

I have tried to find it using the terminal. When I type in:
sudo updatedb
locate firefox
This is my output:
```
/var/lib/dpkg/alternatives/firefox-homepage
/var/lib/dpkg/info/firefox.postinst
/var/lib/dpkg/info/firefox.list
/var/lib/dpkg/info/firefox.preinst
/var/lib/dpkg/info/firefox.prerm
/var/lib/dpkg/info/firefox.postrm
/var/lib/dpkg/info/firefox.conffiles
/var/lib/dpkg/info/firefox.md5sums
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.md5sums
/var/lib/dpkg/info/mozilla-firefox-locale-en-gb.list
/var/lib/mozilla-firefox
/var/lib/mozilla-firefox/extensions.d
/var/lib/mozilla-firefox/extensions.d/50en-GB-locale.ext
/var/cache/apt/archives/libnspr4_2%3a1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_pow erpc.deb
/var/cache/apt/archives/libnss3_2%3a1.firefox1.5.dfsg+1.5.0.8-0ubuntu0.6.06_powe rpc.deb
/var/cache/apt/archives/firefox_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_powerpc.deb
/var/cache/apt/archives/firefox-dbg_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_powerpc.deb
/etc/alternatives/firefox-homepage-locales
/etc/alternatives/firefox-homepage
/etc/firefox
/etc/firefox/firefoxrc
/etc/firefox/profile
/etc/firefox/profile/localstore.rdf
/etc/firefox/profile/search.rdf
/etc/firefox/profile/mimeTypes.rdf
/etc/firefox/profile/prefs.js
/etc/firefox/profile/bookmarks.html
/etc/firefox/profile/chrome
/etc/firefox/profile/chrome/userContent-example.css
/etc/firefox/profile/chrome/userChrome-example.css
/etc/firefox/pref
/etc/firefox/pref/firefox.js
/etc/gre.d/firefox.conf
/usr/share/doc/firefox
/usr/share/doc/firefox/README.Debian.gz
/usr/share/doc/firefox/NEWS.Debian.gz
/usr/share/doc/firefox/copyright
/usr/share/doc/firefox/changelog.Debian.gz
/usr/share/doc/mozilla-thunderbird/mozilla-firefox.js.tmpl
/usr/share/doc/mozilla-firefox-locale-en-gb
/usr/share/doc/mozilla-firefox-locale-en-gb/changelog.Debian.gz
/usr/share/doc/mozilla-firefox-locale-en-gb/copyright
/usr/share/man/man1/mozilla-firefox.1.gz
/usr/share/man/man1/firefox.1.gz
/usr/share/menu/firefox
/usr/share/pixmaps/mozilla-firefox.xpm
/usr/share/pixmaps/firefox.png
/usr/share/pixmaps/mozilla-firefox.png
/usr/share/bug/firefox
/usr/share/bug/firefox/presubj
/usr/share/applications/firefox.desktop
/usr/share/firefox
/usr/share/firefox/defaults
/usr/share/firefox/defaults/autoconfig
/usr/share/firefox/defaults/autoconfig/prefcalls.js
/usr/share/firefox/defaults/autoconfig/platform.js
/usr/share/firefox/defaults/pref
/usr/share/firefox/defaults/pref/channel-prefs.js
/usr/share/firefox/defaults/pref/reporter.js
/usr/share/firefox/defaults/pref/vendor.js
/usr/share/firefox/defaults/pref/firefox.js
/usr/share/firefox/defaults/profile
/usr/share/firefox/defaults/syspref
/usr/share/firefox/chrome
/usr/share/firefox/chrome/browser.jar
/usr/share/firefox/chrome/icons
/usr/share/firefox/chrome/icons/default
/usr/share/firefox/chrome/icons/default/default.xpm
/usr/share/firefox/chrome/browser.manifest
/usr/share/firefox/chrome/comm.jar
/usr/share/firefox/chrome/comm.manifest
/usr/share/firefox/chrome/en-US.jar
/usr/share/firefox/chrome/en-US.manifest
/usr/share/firefox/chrome/toolkit.jar
/usr/share/firefox/chrome/toolkit.manifest
/usr/share/firefox/chrome/pippki.jar
/usr/share/firefox/chrome/pippki.manifest
/usr/share/firefox/chrome/reporter.jar
/usr/share/firefox/chrome/reporter.manifest
/usr/share/firefox/chrome/classic.jar
/usr/share/firefox/chrome/classic.manifest
/usr/share/firefox/searchplugins
/usr/share/firefox/searchplugins/amazondotcom.src
/usr/share/firefox/searchplugins/google.gif
/usr/share/firefox/searchplugins/google.src
/usr/share/firefox/searchplugins/creativecommons.src
/usr/share/firefox/searchplugins/eBay.src
/usr/share/firefox/searchplugins/yahoo.src
/usr/share/firefox/searchplugins/amazondotcom.png
/usr/share/firefox/searchplugins/answers.src
/usr/share/firefox/searchplugins/creativecommons.png
/usr/share/firefox/searchplugins/eBay.gif
/usr/share/firefox/searchplugins/yahoo.gif
/usr/share/firefox/searchplugins/debsearch.gif
/usr/share/firefox/searchplugins/answers.png
/usr/share/firefox/searchplugins/debsearch.src
/usr/share/firefox/searchplugins/wikipedia.gif
/usr/share/firefox/searchplugins/wikipedia.src
/usr/share/firefox/greprefs
/usr/share/firefox/greprefs/security-prefs.js
/usr/share/firefox/greprefs/all.js
/usr/share/firefox/greprefs/xpinstall.js
/usr/share/firefox/res
/usr/share/firefox/res/charsetalias.properties
/usr/share/firefox/res/entityTables
/usr/share/firefox/res/entityTables/htmlEntityVersions.properties
/usr/share/firefox/res/entityTables/html40Latin1.properties
/usr/share/firefox/res/entityTables/html40Symbols.properties
/usr/share/firefox/res/entityTables/html40Special.properties
/usr/share/firefox/res/entityTables/transliterate.properties
/usr/share/firefox/res/entityTables/mathml20.properties
/usr/share/firefox/res/sample.unixpsfonts.properties
/usr/share/firefox/res/charsetData.properties
/usr/share/firefox/res/unixcharset.properties
/usr/share/firefox/res/langGroups.properties
/usr/share/firefox/res/language.properties
/usr/share/firefox/res/forms.css
/usr/share/firefox/res/fonts
/usr/share/firefox/res/fonts/pangoFontEncoding.properties
/usr/share/firefox/res/fonts/fontEncoding.properties
/usr/share/firefox/res/fonts/mathfontPUA.properties
/usr/share/firefox/res/fonts/mathfont.properties
/usr/share/firefox/res/fonts/mathfontCMSY10.properties
/usr/share/firefox/res/fonts/mathfontCMEX10.properties
/usr/share/firefox/res/fonts/mathfontMTExtra.properties
/usr/share/firefox/res/fonts/mathfontMath1.properties
/usr/share/firefox/res/fonts/mathfontMath2.properties
/usr/share/firefox/res/fonts/mathfontMath4.properties
/usr/share/firefox/res/fonts/mathfontSymbol.properties
/usr/share/firefox/res/dtd
/usr/share/firefox/res/dtd/xhtml11.dtd
/usr/share/firefox/res/dtd/mathml.dtd
/usr/share/firefox/res/html.css
/usr/share/firefox/res/hiddenWindow.html
/usr/share/firefox/res/ua.css
/usr/share/firefox/res/viewsource.css
/usr/share/firefox/res/quirk.css
/usr/share/firefox/res/broken-image.gif
/usr/share/firefox/res/arrow.gif
/usr/share/firefox/res/arrowd.gif
/usr/share/firefox/res/html
/usr/share/firefox/res/html/gopher-audio.gif
/usr/share/firefox/res/html/gopher-binary.gif
/usr/share/firefox/res/html/gopher-find.gif
/usr/share/firefox/res/html/gopher-image.gif
/usr/share/firefox/res/html/gopher-menu.gif
/usr/share/firefox/res/html/gopher-movie.gif
/usr/share/firefox/res/html/gopher-sound.gif
/usr/share/firefox/res/html/gopher-telnet.gif
/usr/share/firefox/res/html/gopher-text.gif
/usr/share/firefox/res/html/gopher-unknown.gif
/usr/share/firefox/res/table-add-column-after.gif
/usr/share/firefox/res/loading-image.gif
/usr/share/firefox/res/mathml.css
/usr/share/firefox/res/svg.css
/usr/share/firefox/res/samples
/usr/share/firefox/res/samples/test8-1.html
/usr/share/firefox/res/samples/test0.html
/usr/share/firefox/res/samples/test1.html
/usr/share/firefox/res/samples/test10.html
/usr/share/firefox/res/samples/test11.html
/usr/share/firefox/res/samples/test12.html
/usr/share/firefox/res/samples/test13.html
/usr/share/firefox/res/samples/test14.html
/usr/share/firefox/res/samples/test15.html
/usr/share/firefox/res/samples/test16.html
/usr/share/firefox/res/samples/test2.html
/usr/share/firefox/res/samples/test3.html
/usr/share/firefox/res/samples/test4.html
/usr/share/firefox/res/samples/test5.html
/usr/share/firefox/res/samples/test6.html
/usr/share/firefox/res/samples/test7.html
/usr/share/firefox/res/samples/test8dom.html
/usr/share/firefox/res/samples/test8.html
/usr/share/firefox/res/samples/test_weight.html
/usr/share/firefox/res/samples/test8sca.html
/usr/share/firefox/res/samples/test8siz.html
/usr/share/firefox/res/samples/test8tab.html
/usr/share/firefox/res/samples/test9.html
/usr/share/firefox/res/samples/test9a.html
/usr/share/firefox/res/samples/test9b.html
/usr/share/firefox/res/samples/test_ed.html
/usr/share/firefox/res/samples/test_form.html
/usr/share/firefox/res/samples/test_gfx.html
/usr/share/firefox/res/samples/test_lbox.html
/usr/share/firefox/res/samples/test_pr.html
/usr/share/firefox/res/samples/toolbarTest1.xul
/usr/share/firefox/res/samples/treeTest1.xul
/usr/share/firefox/res/samples/treeTest1.css
/usr/share/firefox/res/samples/sliderTest1.xul
/usr/share/firefox/res/samples/scrollbarTest1.xul
/usr/share/firefox/res/samples/scrollbarTest2.xul
/usr/share/firefox/res/samples/find.html
/usr/share/firefox/res/samples/printsetup.html
/usr/share/firefox/res/samples/image_props.html
/usr/share/firefox/res/samples/aform.css
/usr/share/firefox/res/samples/bform.css
/usr/share/firefox/res/samples/cform.css
/usr/share/firefox/res/samples/demoform.css
/usr/share/firefox/res/samples/mozform.css
/usr/share/firefox/res/samples/xulTest.css
/usr/share/firefox/res/samples/Anieyes.gif
/usr/share/firefox/res/samples/gear1.gif
/usr/share/firefox/res/samples/rock_gra.gif
/usr/share/firefox/res/samples/beeptest.html
/usr/share/firefox/res/samples/soundtest.html
/usr/share/firefox/res/samples/bg.jpg
/usr/share/firefox/res/samples/raptor.jpg
/usr/share/firefox/res/samples/test.wav
/usr/share/firefox/res/samples/checkboxTest.xul
/usr/share/firefox/res/throbber
/usr/share/firefox/res/throbber/anim.gif
/usr/share/firefox/res/throbber/anims00.gif
/usr/share/firefox/res/throbber/anims01.gif
/usr/share/firefox/res/throbber/anims02.gif
/usr/share/firefox/res/throbber/anims03.gif
/usr/share/firefox/res/throbber/anims04.gif
/usr/share/firefox/res/throbber/anims05.gif
/usr/share/firefox/res/throbber/anims06.gif
/usr/share/firefox/res/throbber/anims07.gif
/usr/share/firefox/res/throbber/anims08.gif
/usr/share/firefox/res/throbber/anims09.gif
/usr/share/firefox/res/throbber/anims10.gif
/usr/share/firefox/res/throbber/anims11.gif
/usr/share/firefox/res/throbber/anims12.gif
/usr/share/firefox/res/throbber/anims13.gif
/usr/share/firefox/res/throbber/anims14.gif
/usr/share/firefox/res/throbber/anims15.gif
/usr/share/firefox/res/throbber/anims16.gif
/usr/share/firefox/res/throbber/anims17.gif
/usr/share/firefox/res/throbber/anims18.gif
/usr/share/firefox/res/throbber/anims19.gif
/usr/share/firefox/res/throbber/anims20.gif
/usr/share/firefox/res/throbber/anims21.gif
/usr/share/firefox/res/throbber/anims22.gif
/usr/share/firefox/res/throbber/anims23.gif
/usr/share/firefox/res/throbber/anims24.gif
/usr/share/firefox/res/throbber/anims25.gif
/usr/share/firefox/res/throbber/anims26.gif
/usr/share/firefox/res/throbber/anims27.gif
/usr/share/firefox/res/throbber/anims28.gif
/usr/share/firefox/res/throbber/anims29.gif
/usr/share/firefox/res/viewer.properties
/usr/share/firefox/res/EditorOverride.css
/usr/share/firefox/res/grabber.gif
/usr/share/firefox/res/cmessage.txt
/usr/share/firefox/res/table-add-column-after-active.gif
/usr/share/firefox/res/table-add-column-after-hover.gif
/usr/share/firefox/res/table-add-column-before-active.gif
/usr/share/firefox/res/table-add-column-before-hover.gif
/usr/share/firefox/res/table-add-column-before.gif
/usr/share/firefox/res/table-add-row-after-active.gif
/usr/share/firefox/res/table-add-row-after-hover.gif
/usr/share/firefox/res/table-add-row-after.gif
/usr/share/firefox/res/table-add-row-before-active.gif
/usr/share/firefox/res/table-add-row-before-hover.gif
/usr/share/firefox/res/table-add-row-before.gif
/usr/share/firefox/res/table-remove-column-active.gif
/usr/share/firefox/res/table-remove-column-hover.gif
/usr/share/firefox/res/table-remove-column.gif
/usr/share/firefox/res/table-remove-row-active.gif
/usr/share/firefox/res/table-remove-row-hover.gif
/usr/share/firefox/res/table-remove-row.gif
/usr/share/firefox/icons
/usr/share/firefox/icons/mozicon128.png
/usr/share/firefox/icons/mozicon50.xpm
/usr/share/firefox/icons/mozicon16.xpm
/usr/share/firefox/icons/document.png
/usr/share/firefox/icons/default.xpm
/usr/share/Terminal/apps/firefox.desktop
/usr/share/xfce4/helpers/firefox.desktop
/usr/share/xubuntu-docs/desktopguide/images/C/firefox.png
/usr/bin/firefox
/usr/bin/mozilla-firefox
/usr/bin/firefox.ubuntu
/usr/bin/mozilla-firefox.ubuntu
/usr/lib/mime/packages/firefox
/usr/lib/firefox
/usr/lib/firefox/libgtkembedmoz.so
/usr/lib/firefox/libnssckbi.so
/usr/lib/firefox/libgfxpsshar.so
/usr/lib/firefox/libgkgfx.so
/usr/lib/firefox/libxpcom_compat.so
/usr/lib/firefox/libgtkxtbin.so
/usr/lib/firefox/libjsj.so
/usr/lib/firefox/libmozjs.so
/usr/lib/firefox/firefox
/usr/lib/firefox/pkg-ver
/usr/lib/firefox/libxpcom.so
/usr/lib/firefox/firefox-xremote-client
/usr/lib/firefox/libxpcom_core.so
/usr/lib/firefox/libxpistub.so
/usr/lib/firefox/libsoftokn3.chk
/usr/lib/firefox/components
/usr/lib/firefox/components/xpcom_components.xpt
/usr/lib/firefox/components/xpcom_base.xpt
/usr/lib/firefox/components/xpcom_ds.xpt
/usr/lib/firefox/components/xpcom_io.xpt
/usr/lib/firefox/components/libxpcom_compat_c.so
/usr/lib/firefox/components/xpcom_threads.xpt
/usr/lib/firefox/components/xpcom_xpti.xpt
/usr/lib/firefox/components/proxyObjInst.xpt
/usr/lib/firefox/components/nsProxyAutoConfig.js
/usr/lib/firefox/components/xpcom_obsolete.xpt
/usr/lib/firefox/components/xpconnect.xpt
/usr/lib/firefox/components/libxpconnect.so
/usr/lib/firefox/components/unicharutil.xpt
/usr/lib/firefox/components/uconv.xpt
/usr/lib/firefox/components/libuconv.so
/usr/lib/firefox/components/libucvmath.so
/usr/lib/firefox/components/locale.xpt
/usr/lib/firefox/components/intl.xpt
/usr/lib/firefox/components/lwbrk.xpt
/usr/lib/firefox/components/chardet.xpt
/usr/lib/firefox/components/libi18n.so
/usr/lib/firefox/components/necko.xpt
/usr/lib/firefox/components/necko_viewsource.xpt
/usr/lib/firefox/components/necko_cookie.xpt
/usr/lib/firefox/components/necko_dns.xpt
/usr/lib/firefox/components/necko_socket.xpt
/usr/lib/firefox/components/mimetype.xpt
/usr/lib/firefox/components/necko_strconv.xpt
/usr/lib/firefox/components/necko_cache.xpt
/usr/lib/firefox/components/necko_about.xpt
/usr/lib/firefox/components/necko_data.xpt
/usr/lib/firefox/components/necko_res.xpt
/usr/lib/firefox/components/necko_file.xpt
/usr/lib/firefox/components/necko_http.xpt
/usr/lib/firefox/components/dom_stylesheets.xpt
/usr/lib/firefox/components/necko_ftp.xpt
/usr/lib/firefox/components/libnecko.so
/usr/lib/firefox/components/libnecko2.so
/usr/lib/firefox/components/libjar50.so
/usr/lib/firefox/components/jar.xpt
/usr/lib/firefox/components/uriloader.xpt
/usr/lib/firefox/components/exthandler.xpt
/usr/lib/firefox/components/prefetch.xpt
/usr/lib/firefox/components/pref.xpt
/usr/lib/firefox/components/libpref.so
/usr/lib/firefox/components/caps.xpt
/usr/lib/firefox/components/libcaps.so
/usr/lib/firefox/components/rdf.xpt
/usr/lib/firefox/components/librdf.so
/usr/lib/firefox/components/htmlparser.xpt
/usr/lib/firefox/components/libhtmlpars.so
/usr/lib/firefox/components/gfx.xpt
/usr/lib/firefox/components/libgfxps.so
/usr/lib/firefox/components/libgfx_gtk.so
/usr/lib/firefox/components/imglib2.xpt
/usr/lib/firefox/components/libimglib2.so
/usr/lib/firefox/components/plugin.xpt
/usr/lib/firefox/components/libgkplugin.so
/usr/lib/firefox/components/dom_base.xpt
/usr/lib/firefox/components/dom_canvas.xpt
/usr/lib/firefox/components/dom_core.xpt
/usr/lib/firefox/components/dom_html.xpt
/usr/lib/firefox/components/dom_events.xpt
/usr/lib/firefox/components/dom_traversal.xpt
/usr/lib/firefox/components/dom_views.xpt
/usr/lib/firefox/components/dom_css.xpt
/usr/lib/firefox/components/dom_loadsave.xpt
/usr/lib/firefox/components/dom_range.xpt
/usr/lib/firefox/components/dom_xbl.xpt
/usr/lib/firefox/components/dom_xpath.xpt
/usr/lib/firefox/components/libwidget_gtk2.so
/usr/lib/firefox/components/dom_xul.xpt
/usr/lib/firefox/components/dom_svg.xpt
/usr/lib/firefox/components/dom.xpt
/usr/lib/firefox/components/widget.xpt
/usr/lib/firefox/components/webbrowserpersist.xpt
/usr/lib/firefox/components/content_base.xpt
/usr/lib/firefox/components/content_html.xpt
/usr/lib/firefox/components/content_htmldoc.xpt
/usr/lib/firefox/components/content_xmldoc.xpt
/usr/lib/firefox/components/xuldoc.xpt
/usr/lib/firefox/components/xultmpl.xpt
/usr/lib/firefox/components/content_xslt.xpt
/usr/lib/firefox/components/content_xtf.xpt
/usr/lib/firefox/components/layout_base.xpt
/usr/lib/firefox/components/layout_printing.xpt
/usr/lib/firefox/components/layout_xul.xpt
/usr/lib/firefox/components/layout_xul_tree.xpt
/usr/lib/firefox/components/gksvgrenderer.xpt
/usr/lib/firefox/components/libgklayout.so
/usr/lib/firefox/components/shistory.xpt
/usr/lib/firefox/components/docshell.xpt
/usr/lib/firefox/components/libdocshell.so
/usr/lib/firefox/components/webshell_idls.xpt
/usr/lib/firefox/components/embed_base.xpt
/usr/lib/firefox/components/windowwatcher.xpt
/usr/lib/firefox/components/find.xpt
/usr/lib/firefox/components/libembedcomponents.so
/usr/lib/firefox/components/commandhandler.xpt
/usr/lib/firefox/components/nsHelperAppDlg.js
/usr/lib/firefox/components/progressDlg.xpt
/usr/lib/firefox/components/nsProgressDialog.js
/usr/lib/firefox/components/jsconsole.xpt
/usr/lib/firefox/components/accessibility-atk.xpt
/usr/lib/firefox/components/webBrowser_core.xpt
/usr/lib/firefox/components/libwebbrwsr.so
/usr/lib/firefox/components/editor.xpt
/usr/lib/firefox/components/txtsvc.xpt
/usr/lib/firefox/components/libeditor.so
/usr/lib/firefox/components/libtxmgr.so
/usr/lib/firefox/components/txmgr.xpt
/usr/lib/firefox/components/composer.xpt
/usr/lib/firefox/components/libcomposer.so
/usr/lib/firefox/components/appshell.xpt
/usr/lib/firefox/components/libnsappshell.so
/usr/lib/firefox/components/oji.xpt
/usr/lib/firefox/components/liboji.so
/usr/lib/firefox/components/jsconsole-clhandler.js
/usr/lib/firefox/components/accessibility.xpt
/usr/lib/firefox/components/libaccessibility.so
/usr/lib/firefox/components/chrome.xpt
/usr/lib/firefox/components/libchrome.so
/usr/lib/firefox/components/profile.xpt
/usr/lib/firefox/components/libmork.so
/usr/lib/firefox/components/mozbrwsr.xpt
/usr/lib/firefox/components/directory.xpt
/usr/lib/firefox/components/mozfind.xpt
/usr/lib/firefox/components/libmozfind.so
/usr/lib/firefox/components/nsResetPref.js
/usr/lib/firefox/components/windowds.xpt
/usr/lib/firefox/components/libappcomps.so
/usr/lib/firefox/components/filepicker.xpt
/usr/lib/firefox/components/libfileview.so
/usr/lib/firefox/components/nsFilePicker.js
/usr/lib/firefox/components/libremoteservice.so
/usr/lib/firefox/components/toolkitremote.xpt
/usr/lib/firefox/components/alerts.xpt
/usr/lib/firefox/components/nsCloseAllWindows.js
/usr/lib/firefox/components/autocomplete.xpt
/usr/lib/firefox/components/history.xpt
/usr/lib/firefox/components/passwordmgr.xpt
/usr/lib/firefox/components/satchel.xpt
/usr/lib/firefox/components/fastfind.xpt
/usr/lib/firefox/components/downloads.xpt
/usr/lib/firefox/components/commandlines.xpt
/usr/lib/firefox/components/libcommandlines.so
/usr/lib/firefox/components/appstartup.xpt
/usr/lib/firefox/components/nsExtensionManager.js
/usr/lib/firefox/components/libtoolkitcomps.so
/usr/lib/firefox/components/nsDefaultCLH.js
/usr/lib/firefox/components/toolkitprofile.xpt
/usr/lib/firefox/components/xulapp.xpt
/usr/lib/firefox/components/extensions.xpt
/usr/lib/firefox/components/nsUpdateService.js
/usr/lib/firefox/components/update.xpt
/usr/lib/firefox/components/libuniversalchardet.so
/usr/lib/firefox/components/shellservice.xpt
/usr/lib/firefox/components/xpinstall.xpt
/usr/lib/firefox/components/libxpinstall.so
/usr/lib/firefox/components/jsdservice.xpt
/usr/lib/firefox/components/libjsd.so
/usr/lib/firefox/components/pipboot.xpt
/usr/lib/firefox/components/libpipboot.so
/usr/lib/firefox/components/libpipnss.so
/usr/lib/firefox/components/pipnss.xpt
/usr/lib/firefox/components/pippki.xpt
/usr/lib/firefox/components/libpippki.so
/usr/lib/firefox/components/libcookie.so
/usr/lib/firefox/components/cookie.xpt
/usr/lib/firefox/components/xml-rpc.xpt
/usr/lib/firefox/components/nsDictionary.js
/usr/lib/firefox/components/nsXmlRpcClient.js
/usr/lib/firefox/components/xpti.dat
/usr/lib/firefox/components/xmlextras.xpt
/usr/lib/firefox/components/libxmlextras.so
/usr/lib/firefox/components/autoconfig.xpt
/usr/lib/firefox/components/libautoconfig.so
/usr/lib/firefox/components/libsystem-pref.so
/usr/lib/firefox/components/libtransformiix.so
/usr/lib/firefox/components/nsInterfaceInfoToIDL.js
/usr/lib/firefox/components/websrvcs.xpt
/usr/lib/firefox/components/libpermissions.so
/usr/lib/firefox/components/libwebsrvcs.so
/usr/lib/firefox/components/libauth.so
/usr/lib/firefox/components/libsearchservice.so
/usr/lib/firefox/components/search.xpt
/usr/lib/firefox/components/libbrowserdirprovider.so
/usr/lib/firefox/components/bookmarks.xpt
/usr/lib/firefox/components/libbrowsercomps.so
/usr/lib/firefox/components/migration.xpt
/usr/lib/firefox/components/sidebar.xpt
/usr/lib/firefox/components/nsSidebar.js
/usr/lib/firefox/components/nsBrowserContentHandler.js
/usr/lib/firefox/components/browsercompsbase.xpt
/usr/lib/firefox/components/nsBrowserGlue.js
/usr/lib/firefox/components/compreg.dat
/usr/lib/firefox/firefox-bin
/usr/lib/firefox/searchplugins
/usr/lib/firefox/regxpcom
/usr/lib/firefox/xpcshell
/usr/lib/firefox/xpicleanup
/usr/lib/firefox/xpidl
/usr/lib/firefox/xpt_dump
/usr/lib/firefox/xpt_link
/usr/lib/firefox/firefox.cfg
/usr/lib/firefox/extensions
/usr/lib/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}
/usr/lib/firefox/extensions/{972ce4c6-7e08-4474-a285-3208198ce6fd}/install.rdf
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/install.rdf
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome/en-GB.jar
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/chrome.manifest
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall
/usr/lib/firefox/extensions/langpack-en-GB@firefox.mozilla.org/uninstall/Uninsta ll
/usr/lib/firefox/plugins
/usr/lib/firefox/plugins/libunixprintplugin.so
/usr/lib/firefox/updates
/usr/lib/firefox/updates/0
/usr/lib/firefox/res
/usr/lib/firefox/greprefs
/usr/lib/firefox/defaults
/usr/lib/firefox/chrome
/usr/lib/firefox/icons
/usr/lib/mozilla-firefox
/home/samuel/Desktop/firefox2.sh.txt
/home/samuel/.mozilla/firefox
/home/samuel/.mozilla/firefox/profiles.ini
/home/samuel/.mozilla/firefox/nnc1nzaz.default
/home/samuel/.mozilla/firefox/nnc1nzaz.default/localstore.rdf
/home/samuel/.mozilla/firefox/nnc1nzaz.default/search.rdf
/home/samuel/.mozilla/firefox/nnc1nzaz.default/mimeTypes.rdf
/home/samuel/.mozilla/firefox/nnc1nzaz.default/prefs.js
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarks.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/chrome
/home/samuel/.mozilla/firefox/nnc1nzaz.default/chrome/userContent-example.css
/home/samuel/.mozilla/firefox/nnc1nzaz.default/chrome/userChrome-example.css
/home/samuel/.mozilla/firefox/nnc1nzaz.default/.parentlock
/home/samuel/.mozilla/firefox/nnc1nzaz.default/compatibility.ini
/home/samuel/.mozilla/firefox/nnc1nzaz.default/compreg.dat
/home/samuel/.mozilla/firefox/nnc1nzaz.default/xpti.dat
/home/samuel/.mozilla/firefox/nnc1nzaz.default/extensions
/home/samuel/.mozilla/firefox/nnc1nzaz.default/extensions.rdf
/home/samuel/.mozilla/firefox/nnc1nzaz.default/extensions.cache
/home/samuel/.mozilla/firefox/nnc1nzaz.default/extensions.ini
/home/samuel/.mozilla/firefox/nnc1nzaz.default/secmod.db
/home/samuel/.mozilla/firefox/nnc1nzaz.default/cert8.db
/home/samuel/.mozilla/firefox/nnc1nzaz.default/key3.db
/home/samuel/.mozilla/firefox/nnc1nzaz.default/history.dat
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks-2006-12 -15.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks-2006-12 -16.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks-2006-12 -18.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks-2006-12 -13.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks-2006-12 -14.html
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/_CACHE_MAP_
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/_CACHE_001_
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/_CACHE_002_
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/_CACHE_003_
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/AAA763D4d01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/A89F4DBCd01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/9544A905d01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/8FF5D29Dd01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/40D4F5F3d01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/Cache/E05FFDFAd01
/home/samuel/.mozilla/firefox/nnc1nzaz.default/bookmarks.bak
/home/samuel/.mozilla/firefox/nnc1nzaz.default/formhistory.dat
/home/samuel/.mozilla/firefox/nnc1nzaz.default/cookies.txt
/home/samuel/.mozilla/firefox/pluginreg.dat
/home/samuel/.mozilla_backup/firefox
/home/samuel/.mozilla_backup/firefox/profiles.ini
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/localstore.rdf
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/search.rdf
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/mimeTypes.rdf
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/prefs.js
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarks.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/chrome
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/chrome/userContent-example .css
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/chrome/userChrome-example. css
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/.parentlock
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/compatibility.ini
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/compreg.dat
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/xpti.dat
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/extensions
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/extensions.rdf
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/extensions.cache
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/extensions.ini
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/XUL.mfasl
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/secmod.db
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/cert8.db
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/key3.db
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/history.dat
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks- 2006-12-15.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks- 2006-12-16.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks- 2006-12-18.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks- 2006-12-13.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarkbackups/bookmarks- 2006-12-14.html
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/_CACHE_MAP_
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/_CACHE_001_
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/_CACHE_002_
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/_CACHE_003_
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/AAA763D4d01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/A89F4DBCd01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/9544A905d01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/8FF5D29Dd01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/40D4F5F3d01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/Cache/E05FFDFAd01
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/bookmarks.bak
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/formhistory.dat
/home/samuel/.mozilla_backup/firefox/nnc1nzaz.default/cookies.txt
/home/samuel/.mozilla_backup/firefox/pluginreg.dat
```
If someone could tell me which one of these files is the actual application that would be a great help. There are a number of files called 'Firefox' or 'Mozilla.firefox' but all the ones I have found appear to be broken links, not the application itself. One link was to a file in /opt that I assume would have been the original application, but my /opt folder is empty. 

I cannot find it using the application finder nor run it from "Run Program" in the menu. I have also installed the R statistical package and cannot find it either, possibly for a similar reason, but Firefox is my most pressing need at the moment. Any ideas what I can do?

---

### Post by pay on 2006-12-19
Your firefox installation resides here "/usr/lib/firefox"

---

### Post by bionnaki on 2006-12-19
how did you originally install it?

---

### Post by samden on 2006-12-19
It was originally installed with my Xubuntu installation.

Thanks for pointing out where the application lives! I can now open it, although it just crashed on me again... Can sort out the crashing issue later though. How can I get XFCE to recognise that it exists, show it in the application menu and get the toolbar button to work?

---

### Post by pay on 2006-12-19
Can you run it in the terminal and post the error message?

---

### Post by samden on 2006-12-19
How do I run firefox in the terminal?

---

### Post by pay on 2006-12-19
Open up the terminal and try typing in ```
firefox
```If that doesn't work try```
sh /usr/lib/firefox/firefox
```

---

### Post by jic on 2006-12-19
from your output:

 /usr/bin/firefox
 /usr/bin/mozilla-firefox
 /usr/bin/firefox.ubuntu
 /usr/bin/mozilla-firefox.ubuntu

otherwise try a "powerfull" locate

$locate firefox | grep bin

---

### Post by samden on 2006-12-19
> **pay said:**
> Open up the terminal and try typing in ```
firefox
```If that doesn't work try```
sh /usr/lib/firefox/firefox
```
When I type in:

firefox

```
bash: firefox: command not found
```

sh /usr/lib/firefox/firefox

Firefox opens, just like when I open it normally. No more text shows in the terminal - the cursor sits at the start of a new line, no command prompt.

---

### Post by samden on 2006-12-19
> **jic said:**
> from your output:

 /usr/bin/firefox
 /usr/bin/mozilla-firefox
 /usr/bin/firefox.ubuntu
 /usr/bin/mozilla-firefox.ubuntu

otherwise try a "powerfull" locate

$locate firefox | grep bin
/usr/bin/firefox and /usr/bin/mozilla-firefox are broken links to /opt/firefox/firefox. My /opt folder is empty.

/usr/bin/firefox.ubuntu and /usr/bin/mozilla-firefox.ubuntu are links that opens firefox. According to the preferences they are each a link to shell script ../lib/firefox/firefox.

What I need to do is tell XFCE4 that Firefox exists, so it will open from the applications menu and the button in the top menu bar. How do I do this?

---

### Post by pay on 2006-12-19
You can always make a command for it.```
sudo nano /usr/bin/firefox
```and add something like this in```
#!/bin/sh
sh /usr/lib/firefox/firefox
``````
sudo chmod 755 /usr/bin/firefox
```though this is not the desirable way to do it.

---

### Post by samden on 2006-12-19
What will that actually do? Will that make a new icon in the menubar, or a key command that will open it, or what?

---

### Post by pay on 2006-12-19
It would make a command, that when you executed it, it would open firefox.

---

### Post by samden on 2006-12-19
Edit: Forget all that, my mistake. I have edited the correct file now.

After following the instructions above, I enter the command firefox into Terminal - nothing happens. I enter into Run program - Error. "failed to execute child process "firefox" (No such file or directory)".

---

### Post by raul_ on 2006-12-19
```

nano <path>/<name of the new file>

```

---

### Post by samden on 2006-12-19
> **pay said:**
> Your firefox installation resides here "/usr/lib/firefox"
I have created a link to /usr/lib/firefox and placed it on the desktop. Sometimes this will open Firefox, and sometimes it will not. Normally I double click on it, the hard drive makes a couple of minor noises, and nothing happens. However sometimes Firefox will open fine from this link. The same goes for /usr/lib/firefox - often nothing happens when I double click on it, but sometimes Firefox opens fine. Why could this be so unstable and unpredictable? :confused:

---

### Post by samden on 2006-12-20
As I have so many problems I am reinstalling the system. This will probably take a number of days or weeks based on my previous experience installing on this computer. So don't worry about this issue any more - I'm sure I'll have other things to worry about with my installation instead! Thanks for your help.

---

