---
title: "Remove entries from main menu"
date: 2008-02-03
forum: General Help
---

### Post by dbostream on 2008-02-03
Hi I have read a couple of other threads about this but I have been unsuccessful to solve this problem.

Anyway, I managed to add too many entries for a program I installed under Applications in the main menu and now I can't remove them. As I'm new to ubuntu I have no idea how to remove them, I couldn't find a remove button. I have tried to go to Systems>Preferences>Main Menu and uncheck them but they are not there!

I have uploaded an image and circled the entries I want removed:

[IMG]http://i249.photobucket.com/albums/gg209/mapleleafs1967/mainmenu.png[/IMG]

It didn't help to uninstall the application.

I would appreciate any help.

---

### Post by jrib on 2008-02-03
Are they still there after you logged out and back in after reinstalling?

---

### Post by dbostream on 2008-02-03
Yes they are.

---

### Post by jrib on 2008-02-03
paste results of:
```
locate netbeans.desktop
```

---

### Post by dbostream on 2008-02-03
I got nothing.

I tried the same thing for another application and it gave me two locations.

I wonder what's going on.

And according to this, the Programming submeny isen't even suppose to be showing but it does.

[IMG]http://i249.photobucket.com/albums/gg209/mapleleafs1967/alacarte.png[/IMG]

---

### Post by jrib on 2008-02-05
Hmm, we have to figure out where they are coming from.  Lets try ```
locate netbeans
``` and see if we get lucky

---

### Post by dbostream on 2008-02-06
This is what I got:

```
/home/dabo/netbeans-6.0/cnd1/modules/org-netbeans-modules-cnd-modelui.jar
/home/dabo/netbeans-6.0/cnd1/modules/org-netbeans-modules-cnd.jar
/home/dabo/netbeans-6.0/cnd1/modules/org-netbeans-modules-cnd-qnavigator.jar
/home/dabo/netbeans-6.0/cnd1/modules/org-netbeans-modules-cnd-highlight.jar
/home/dabo/netbeans-6.0/cnd1/modules/org-netbeans-modules-cnd-repository.jar
/home/dabo/netbeans-6.0/bin
/home/dabo/netbeans-6.0/bin/netbeans
/home/dabo/netbeans-6.0/bin/netbeans.exe
/home/dabo/netbeans-6.0/bin/nb.exe
/home/dabo/netbeans-6.0/netbeans.css
/home/dabo/netbeans-6.0/DISTRIBUTION.txt
/home/dabo/netbeans-6.0/ide8
/home/dabo/netbeans-6.0/ide8/docs
/home/dabo/netbeans-6.0/ide8/docs/html-4.01.zip
/home/dabo/netbeans-6.0/ide8/docs/org
/home/dabo/netbeans-6.0/ide8/docs/org/netbeans
/home/dabo/netbeans-6.0/ide8/docs/org/netbeans/modules
/home/dabo/netbeans-6.0/ide8/docs/org/netbeans/modules/usersguide
/home/dabo/netbeans-6.0/ide8/docs/org/netbeans/modules/usersguide/ide.css
/home/dabo/netbeans-6.0/ide8/update_tracking
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-core.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-highlights.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-plain-lib.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-retriever.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-core-ide.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-tasklist-projectint.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-openidex-util.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-bat.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-servletapi.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-lib-cvsclient.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-palette.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-svnClientAdapter.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-fold.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db-core.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-css-visual.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db-kit.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-javascript.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-projectuiapi.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-axi.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-errorstripe-api.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db-sql-editor.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-properties-syntax.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-xam.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-html-editor-lib.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-wsdl-model.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-gototest.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-settings-storage.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-commons_logging.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-xerces.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-catalog.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xsl.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-web-flyingsaucer.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-css.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-refactoring-api.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-bookmarks.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-guards.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-image.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db-sql-visualeditor.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-lib2.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-versioning-util.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-project-libraries.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-swing-dirchooser.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-versioning.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-navigator.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-bracesmatching.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-project-ant.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-ini4j.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-manifest.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-jumpto.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-jsch.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-utilities-project.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-lexer-nbbridge.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-ide-kit.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-text.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-schema2beans.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-properties.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-util.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-projectui.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-multiview.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-viewmodel.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-tax.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-errorstripe.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-tasklist-todo.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-subversion.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-options-editor.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-indent.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-schema-model.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-html-lexer.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-diff.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-apache-xml-resolver.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-httpserver.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-versioning-system-cvss.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-api-xml.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-kit.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-defaults.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-plain.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-tasklist-ui.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-completion.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-lexer.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-api-debugger.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-tasklist.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-html.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-classfile.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-languages-sh.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-editor-hints.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-projectapi.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-dbapi.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-freemarker.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-lib.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-db-drivers.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-lexer.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-usersguide.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-extbrowser.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-schema-completion.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-xdm.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-libs-lucene.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-codetemplates.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-structure.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-xml-tools.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-editor-settings.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-tasklist-kit.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-spi-debugger-ui.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-utilities.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-diff.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-html-editor.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-lexer-editorbridge.xml
/home/dabo/netbeans-6.0/ide8/update_tracking/org-netbeans-modules-localhistory.xml
/home/dabo/netbeans-6.0/ide8/config
/home/dabo/netbeans-6.0/ide8/config/Modules
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-core.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-highlights.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-plain-lib.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-retriever.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-core-ide.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-tasklist-projectint.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-openidex-util.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-bat.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-servletapi.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-lib-cvsclient.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-palette.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-svnClientAdapter.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-fold.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db-core.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-css-visual.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db-kit.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-javascript.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-projectuiapi.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-axi.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-errorstripe-api.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db-sql-editor.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-properties-syntax.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-xam.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-html-editor-lib.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-wsdl-model.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-gototest.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-settings-storage.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-commons_logging.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-xerces.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-catalog.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xsl.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-web-flyingsaucer.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-css.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-refactoring-api.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-bookmarks.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-guards.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-image.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db-sql-visualeditor.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-lib2.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-versioning-util.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-project-libraries.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-swing-dirchooser.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-versioning.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-navigator.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-bracesmatching.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-project-ant.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-ini4j.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-manifest.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-jumpto.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-jsch.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-utilities-project.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-lexer-nbbridge.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-ide-kit.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-text.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-schema2beans.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-properties.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-util.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-projectui.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-multiview.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-viewmodel.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-tax.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-errorstripe.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-tasklist-todo.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-subversion.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-options-editor.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-indent.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-schema-model.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-html-lexer.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-diff.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-apache-xml-resolver.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-httpserver.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-versioning-system-cvss.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-api-xml.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-kit.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-defaults.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-plain.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-tasklist-ui.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-completion.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-lexer.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-api-debugger.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-tasklist.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-html.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-classfile.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-languages-sh.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-editor-hints.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-projectapi.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-dbapi.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-freemarker.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-lib.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-db-drivers.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-lexer.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-usersguide.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-extbrowser.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-schema-completion.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-xdm.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-libs-lucene.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-codetemplates.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-structure.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-xml-tools.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-editor-settings.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-tasklist-kit.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-spi-debugger-ui.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-utilities.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-diff.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-html-editor.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-lexer-editorbridge.xml
/home/dabo/netbeans-6.0/ide8/config/Modules/org-netbeans-modules-localhistory.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-spi-palette.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-modules-projectuiapi.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-modules-project-libraries.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-modules-project-ant.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-modules-db.xml
/home/dabo/netbeans-6.0/ide8/config/ModuleAutoDeps/org-netbeans-modules-projectapi.xml
/home/dabo/netbeans-6.0/ide8/modules
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-html-editor-lib.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-lucene.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-bookmarks.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-gototest.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-lexer-editorbridge.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-schema-completion.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-indent.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-palette.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-tasklist.jar
/home/dabo/netbeans-6.0/ide8/modules/docs
/home/dabo/netbeans-6.0/ide8/modules/docs/org-netbeans-modules-usersguide.jar
/home/dabo/netbeans-6.0/ide8/modules/docs/org-netbeans-modules-versioning-system-cvss.jar
/home/dabo/netbeans-6.0/ide8/modules/docs/org-netbeans-modules-db.jar
/home/dabo/netbeans-6.0/ide8/modules/docs/org-netbeans-modules-subversion.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-bat.jar
/home/dabo/netbeans-6.0/ide8/modules/org-openidex-util.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-lexer.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-svnClientAdapter.jar
/home/dabo/netbeans-6.0/ide8/modules/lib
/home/dabo/netbeans-6.0/ide8/modules/lib/extbrowser64.dll
/home/dabo/netbeans-6.0/ide8/modules/lib/extbrowser.dll
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db-sql-editor.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-util.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-image.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-usersguide.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-sh.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-xdm.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-versioning-system-cvss.jar
/home/dabo/netbeans-6.0/ide8/modules/org-apache-xml-resolver.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-highlights.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-javascript.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db-core.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-viewmodel.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-lexer.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-jsch.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-editor-hints.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-dbapi.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-versioning-util.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-projectuiapi.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-jumpto.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-css-visual.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-lexer-nbbridge.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-defaults.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-debugger-ui.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-localhistory.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-diff.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-classfile.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-lib.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-codetemplates.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-errorstripe-api.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-axi.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-xerces.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db-kit.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-html.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-servletapi.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-kit.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-structure.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db-drivers.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-spi-navigator.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-projectapi.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-freemarker.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-xam.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-httpserver.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-properties.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-plain-lib.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-ini4j.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-tasklist-todo.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-plain.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-utilities-project.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-api-debugger.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-extbrowser.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-tools.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-core.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-refactoring-api.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-web-flyingsaucer.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-retriever.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-project-ant.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-tasklist-kit.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-tasklist-projectint.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-errorstripe.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-properties-syntax.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-api-xml.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-tax.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db-sql-visualeditor.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-libs-commons_logging.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-project-libraries.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-lib-cvsclient.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-utilities.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-settings.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-guards.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-completion.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-db.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-settings-storage.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-text.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-fold.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-projectui.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-bracesmatching.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-html-editor.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-ide-kit.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xsl.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-subversion.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-manifest.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-schema-model.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-multiview.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-tasklist-ui.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-html-lexer.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-catalog.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-core-ide.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-versioning.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-diff.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-swing-dirchooser.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-xml-wsdl-model.jar
/home/dabo/netbeans-6.0/ide8/modules/ext
/home/dabo/netbeans-6.0/ide8/modules/ext/freemarker-2.3.8.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/core-renderer.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/svnClientAdapter-0.9.23.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/ddl.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/org-netbeans-tax.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/servlet-2.2.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/mysql-connector-java-5.0.7-bin.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/xerces-2.8.0.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/resolver-1.2.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/lucene-core-2.1.0.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/postgresql-8.2-506.jdbc3.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/commons-logging-1.0.4.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/flute-1.3.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/jsch-0.1.24.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/ini4j-0.2.6.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/sac-1.3.jar
/home/dabo/netbeans-6.0/ide8/modules/ext/webserver.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-schema2beans.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-options-editor.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-editor-lib2.jar
/home/dabo/netbeans-6.0/ide8/modules/org-netbeans-modules-languages-css.jar

```

---

### Post by jrib on 2008-02-06
ok, at least that tells us it's in your HOME.  What does this command return:

```
ls ~/.local/share/applications/
```

---

### Post by dbostream on 2008-02-06
Here's the result:

```
dabo@dabo-laptop:~$ ls ~/.local/share/applications/
alacarte-made-1.desktop   gnomecc.desktop
alacarte-made-2.desktop   nautilus-file-management-properties.desktop
alacarte-made.desktop     netbeans-6.0.desktop
bug-buddy.desktop         python2.5.desktop
gnome-btdownload.desktop

```

I forgot to mention, I re-installed netbeans because I needed it in school, and now I got a "good" entry under programming. The circled one on this image, still though, I want the other netbeans gone.

[IMG]http://i249.photobucket.com/albums/gg209/mapleleafs1967/mainmenu2.png[/IMG]

---

### Post by TheBoat on 2008-02-06
Just go to System -> Preferences -> Main Menu, select programming on the left side, and then uncheck the box of the program you no longer want to appear in the list.

---

### Post by dbostream on 2008-02-06
> **TheBoat said:**
> Just go to System -> Preferences -> Main Menu, select programming on the left side, and then uncheck the box of the program you no longer want to appear in the list.

As I've said earlier, there is nothing to uncheck, take a look at this image:

[IMG]http://i249.photobucket.com/albums/gg209/mapleleafs1967/alacarte.png[/IMG]

---

### Post by TheBoat on 2008-02-06
Sorry, I didn't notice that in your second screenshot.

---

### Post by jrib on 2008-02-06
k, open up those three "alacarte-made" files in a text editor and see if they are about netbeans.

If that fails, let this run for a few minutes: 
```
for file in $(locate .desktop); do grep -H netbean $file 2> /dev/null; done
```

---

### Post by dbostream on 2008-02-07
I finally found them, they were in:

```
~/.local/share/applications/
```

I deleted them and now everything looks like I want it to.

Thank you very much for all your help,

---

### Post by jrib on 2008-02-07
cool, no problem

---

