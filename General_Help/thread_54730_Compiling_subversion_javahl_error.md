---
title: "Compiling subversion javahl error"
date: 2005-08-05
forum: General Help
---

### Post by kismet-sl on 2005-08-05
Hi All,
I have two quetion:
1 -  Why javahl library is not included inside subversion package?
2 - I'm trying to compile the library by myself with the following command, but I get error. Any clue?

user@host: ./configure --enable-javahl --without-apache --without-swing --with-apr=/usr/ --with-apr-util=/usr/
user@host: make (that compile with no error)
user@host: make javahl
none  -d subversion/bindings/java/javahl/classes -classpath subversion/bindings/java/javahl/classes: /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/DirEntry.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNClient.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/ScheduleKind.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNInputStream.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/NotifyAction.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNOutputStream.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/PromptUserPassword2.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/Status.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/PromptUserPassword3.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNClientSynchronized.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/NotifyStatus.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/CommitItemStateFlags.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/JNIError.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNClientInterface.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/ClientException.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/Notify.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/CommitItem.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/PromptUserPassword.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNAdmin.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/NodeKind.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/RevisionKind.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/Info.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/LogMessage.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/StatusKind.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/Revision.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/PropertyData.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/OutputInterface.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/SVNClientLogLevel.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/ChangePath.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/InputInterface.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/BlameCallback.java /opt/src/subversion-1.1.1/subversion/bindings/java/javahl/src/org/tigris/subversion/javahl/CommitMessage.java

make: none: Command not found
make: *** [javahl-java] Error 127

---

### Post by kismet-sl on 2005-08-06
I found the erro by myself. Here there is a little trubleshooting guide:

ERROR:
if you get **none -d** as comman runned by **make javahl** means that **./confiugre** wasn't able to find your JDK
FIX:
Run again **./configure **with the additional param **--with-jdk=<path to java home>**

ERROR:
make javahl fail beacuse doesn't find DirEntry.classs
FIX
The **make javahl** file doesn't create the deploy struct, you have to create the directory with **mkdir subversion/bindings/java/javahl/classes**

---

