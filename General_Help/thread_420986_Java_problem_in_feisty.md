---
title: "Java problem in feisty"
date: 2007-04-24
forum: General Help
---

### Post by cityhawk on 2007-04-24
Yesterday, I've updated my edgy to feisty. So my java6 is broken now. I can't launch netbeans neither other java software

$ /usr/bin/netbeans                                                                                                    /usr/share/netbeans/5.5/bin/../platform6/lib/nbexec: line 422: 19544 [COLOR="Red"]Segmentation fault[/COLOR]      (core dumped) "/usr/bin/java" -Djdk.home="/usr" -classpath "/usr/share/netbeans/5.5/platform6/lib/boot.jar:/usr/share/netbeans/5.5/platform6/lib/org-openide-modules.jar:/usr/share/netbeans/5.5/platform6/lib/org-openide-util.jar" -Dnetbeans.osenv="/tmp/nbenv.19491" -Dnetbeans.osenv.nullsep=true -Dnetbeans.system_http_proxy="DIRECT" -Dnetbeans.system_http_non_proxy_hosts="" -Dnetbeans.dirs="/usr/share/netbeans/5.5/bin/../nb5.5:/usr/share/netbeans/5.5/bin/../ide7:/usr/share/netbeans/5.5/bin/../enterprise3:/usr/share/netbeans/5.5/bin/../harness:" -Dnetbeans.home="/usr/share/netbeans/5.5/platform6" "-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade" "-Dnetbeans.accept_license_class=org.netbeans.license.AcceptLicense" "-Xms32m" "-Xmx128m" "-XX:PermSize=32m" "-XX:MaxPermSize=160m" "-Xverify:none" "-Dapple.laf.useScreenMenuBar=true" org.netbeans.Main --userdir "/home/cityhawk/.netbeans/5.5" "--branding" "nb"

Googling a bit, I've found that some people have the same problem. Is there a working solution for this?

$ java -version                                                                                                        
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

