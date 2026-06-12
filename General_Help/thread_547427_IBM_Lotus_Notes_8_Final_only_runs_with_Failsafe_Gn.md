---
title: "IBM Lotus Notes 8 Final only runs with Failsafe Gnome"
date: 2007-09-10
forum: General Help
---

### Post by ev0 on 2007-09-10
Hi all,
I finally installed Lotus Notes 8 final but it only runs with failsafe gnome. With a regular login, every time I launch Notes there's a JVM crash. The error message is posted below.

I'm trying to find what's the difference between a failsafe gnome start and a regular start. Does anyone have any clue or any similar experience? How can I check what's loaded with a regular start and what's not with a failsafe? Thanks!

```
JVM terminated. Exit code=160
/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200707311521/jre/bin/notes2w
-Xmx512m
-Xquickstart
-Xjit:noResumableTrapHandler
-Dosgi.framework.extensions=com.ibm.rcp.core.logger.frameworkhook,com.ibm.cds
-Xscmx64m
-Xshareclasses:name=xpdplat%g,groupAccess,keep,nonfatal
-Drcp.home=/opt/ibm/lotus/notes/framework
-Drcp.data=/home/houyr/lotus/notes/data/workspace
-Dosgi.splashPath=platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl1,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl2,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl3
-Dcom.ibm.rcp.install.id=1189233555789
-Drcp.install.config=multiuser
-Declipse.registry.nulltoken=true
-Dautopd.logfile.generations=3
-Dorg.apache.xerces.xni.parser.XMLParserConfiguration=org.apache.xerces.parsers.XIncludeAwareParserConfiguration
-Dautopd.instance.area=/home/houyr/lotus/notes/data/workspace/autopd/
-Disa.ignoreESR=true
-Djava.util.logging.config.class=com.ibm.rcp.core.internal.logger.boot.LoggerConfig
-Dcom.ibm.pvc.webcontainer.port=0
-Disa.ignorePortableCollector=true
-Disa.ignoreFeedback=true
-Disa.ignoreUpdate=true
-Dderby.stream.error.file=/home/houyr/lotus/notes/data/workspace/logs/derby.log
-Djava.security.properties=file:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/rcp.security.properties
-Djava.protocol.handler.pkgs=com.ibm.net.ssl.www.protocol
-Dosgi.hook.configurators.exclude=org.eclipse.core.runtime.internal.adaptor.EclipseLogHook
-Drcp.osgi.install.area=/opt/ibm/lotus/notes/framework/eclipse
-Xbootclasspath/a:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/rcpbootcp.jar
-jar /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/launcher.jar
-os linux
-ws gtk
-arch x86
-launcher /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/linux/x86/eclipse
-name IBM Lotus Notes
-showsplash 600
-exitdata 35801c
-nl en_US
-dir ltr
-personality com.ibm.rcp.platform.personality
-product com.ibm.notes.branding.notes
-data /home/houyr/lotus/notes/data/workspace
-configuration /home/houyr/lotus/notes/data/workspace/.config
-plugincustomization /opt/ibm/lotus/notes/framework/rcp/plugin_customization.ini
-vm /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.j2se.linux.x86_1.5.0.SR4-200707311521/jre/bin/notes2w
-vmargs
-Xmx512m
-Xquickstart
-Xjit:noResumableTrapHandler
-Dosgi.framework.extensions=com.ibm.rcp.core.logger.frameworkhook,com.ibm.cds
-Xscmx64m
-Xshareclasses:name=xpdplat%g,groupAccess,keep,nonfatal
-Drcp.home=/opt/ibm/lotus/notes/framework
-Drcp.data=/home/houyr/lotus/notes/data/workspace
-Dosgi.splashPath=platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl1,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl2,platform:/base/../shared/eclipse/plugins/com.ibm.notes.branding.nl3
-Dcom.ibm.rcp.install.id=1189233555789
-Drcp.install.config=multiuser
-Declipse.registry.nulltoken=true
-Dautopd.logfile.generations=3
-Dorg.apache.xerces.xni.parser.XMLParserConfiguration=org.apache.xerces.parsers.XIncludeAwareParserConfiguration
-Dautopd.instance.area=/home/houyr/lotus/notes/data/workspace/autopd/
-Disa.ignoreESR=true
-Djava.util.logging.config.class=com.ibm.rcp.core.internal.logger.boot.LoggerConfig
-Dcom.ibm.pvc.webcontainer.port=0
-Disa.ignorePortableCollector=true
-Disa.ignoreFeedback=true
-Disa.ignoreUpdate=true
-Dderby.stream.error.file=/home/houyr/lotus/notes/data/workspace/logs/derby.log
-Djava.security.properties=file:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/rcp.security.properties
-Djava.protocol.handler.pkgs=com.ibm.net.ssl.www.protocol
-Dosgi.hook.configurators.exclude=org.eclipse.core.runtime.internal.adaptor.EclipseLogHook
-Drcp.osgi.install.area=/opt/ibm/lotus/notes/framework/eclipse
-Xbootclasspath/a:/opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/rcpbootcp.jar
-jar /opt/ibm/lotus/notes/framework/rcp/eclipse/plugins/com.ibm.rcp.base_6.1.1.200707311521/launcher.jar 
```

---

### Post by kekegg on 2007-09-20
add -kill option to the start command line

---

### Post by Silx on 2007-10-08
Do you happen to know where I could get Lotus Notes 8 Final for linux? I want to try and get it running on Ubuntu. I can't find it anywhere! >:|

---

