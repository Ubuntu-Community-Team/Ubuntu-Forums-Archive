---
title: "jdownloader stopped working"
date: 2013-01-15
forum: General Help
---

### Post by rogerdv on 2013-01-15
This morning I was trying to install language support for my recently reinstalled 12.04.1. I didnt completed the download, but anyway it made a long process involving a lot of packages. After that, I was asked to restart 2 times, and then I found that jdownloader no longer works. Ther eis no error in the logs, just this:

```
roger@gaara:~/downloads/jdown$ ./jd.sh
JD Installation found: Starting JD now

------------------------  Thread: 10  -----------------------
10 15/01/13 10:51:07 - INFO [jd.Main(main)] -> Start JDownloader
JAR
10 15/01/13 10:51:07 - FINEST [jd.utils.JDUtilities(getJDClassLoader)] -> Create Classloader: for: /home/roger/.jd
10 15/01/13 10:51:07 - FINEST [jd.JDClassLoader(<init>)] -> rootDir:/home/roger/.jd
/home/roger/.jd
 file:/home/roger/.jd/jd
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDRemoteControl.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDInfoFileWriter.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDExternInterface.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDChat.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDHTTPLiveHeaderScripter.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDUnrar.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/schedule.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDShutdown.jar
10 15/01/13 10:51:07 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDGrowl.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDHJMerge.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDPackageCustomizer.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDFolderWatch.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDWebinterface.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDLangFileEditor.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/plugins/JDTray.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Jar file loaded: /home/roger/.jd/JDownloader.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaSimple2D.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlueIce.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/substance-swingx.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaWhiteVision.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlueSteel.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/synthetica.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlueMoon.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaSkyMetallic.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaMauveMetallic.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBatik.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlackStar.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaSilverMoon.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaGreenDream.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/substance.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlackEye.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaBlackMoon.jar
10 15/01/13 10:51:08 - FINER [jd.JDClassLoader(<init>)] -> Look and Feel JAR loaded: /home/roger/.jd/libs/laf/syntheticaOrangeMetallic.jar
```

---

