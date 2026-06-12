---
title: "Java WebStart apps failing validation"
date: 2007-06-07
forum: General Help
---

### Post by Hikaru79 on 2007-06-07
I'm trying to run some Java Web Start apps that I *know for a fact* are safe and previously worked before Feisty/JVM6. However, they all fail with validation errors when I try to run them now.

I am run sun-java6-jdk. The errors are reproduced here:
```
adrian@adrian-desktop:~$ javaws -verbose cgoban.jnlp
Java(TM) Web Start 1.6.0 Launching: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java
/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java
 -Xbootclasspath/a:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/javaws.jar:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/deploy.jar
 -classpath
 /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/deploy.jar
 -Djava.security.policy=file:/usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/security/javaws.policy
 -DtrustProxy=true
 -Xverify:remote
 -Djnlpx.home=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin
 -Djnlpx.remove=true
 -Xmx150m
 -Djnlpx.heapsize=NULL,150m
 -Djnlpx.splashport=45985
 -Djnlpx.jvm=/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java
 com.sun.javaws.Main
 /tmp/javawqSe2kc
```

The stack trace from the thrown exception (displayed by the boot dialog thinger) is as follows:
```
sun.security.validator.ValidatorException: PKIX path validation failed: java.security.cert.CertPathValidatorException: Must specify the location of an OCSP Responder
    at sun.security.validator.PKIXValidator.doValidate(PKIXValidator.java:251)
    at sun.security.validator.PKIXValidator.doValidate(PKIXValidator.java:234)
    at sun.security.validator.PKIXValidator.engineValidate(PKIXValidator.java:148)
    at sun.security.validator.Validator.validate(Validator.java:218)
    at sun.security.validator.Validator.validate(Validator.java:187)
    at com.sun.deploy.security.TrustDecider.isAllPermissionGranted(TrustDecider.java:392)
    at com.sun.javaws.security.AppPolicy.grantUnrestrictedAccess(AppPolicy.java:211)
    at com.sun.javaws.LaunchDownload.checkSignedResourcesHelper(LaunchDownload.java:1238)
    at com.sun.javaws.LaunchDownload.checkSignedResources(LaunchDownload.java:1075)
    at com.sun.javaws.Launcher.prepareLaunchFile(Launcher.java:620)
    at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:165)
    at com.sun.javaws.Launcher.launch(Launcher.java:95)
    at com.sun.javaws.Main.launchApp(Main.java:299)
    at com.sun.javaws.Main.continueInSecureThread(Main.java:209)
    at com.sun.javaws.Main$1.run(Main.java:106)
    at java.lang.Thread.run(Thread.java:619)
Caused by: java.security.cert.CertPathValidatorException: Must specify the location of an OCSP Responder
    at sun.security.provider.certpath.PKIXMasterCertPathValidator.validate(PKIXMasterCertPathValidator.java:139)
    at sun.security.provider.certpath.PKIXCertPathValidator.doValidate(PKIXCertPathValidator.java:316)
    at sun.security.provider.certpath.PKIXCertPathValidator.engineValidate(PKIXCertPathValidator.java:178)
    at java.security.cert.CertPathValidator.validate(CertPathValidator.java:250)
    at sun.security.validator.PKIXValidator.doValidate(PKIXValidator.java:246)
    ... 15 more
```

I have not made any changes to the default security settings for Java6, so I don't think that's what's causing the problem, but then again, I don't actually know =/

I emphasize again that I have been running these apps in Linux for years before upgrading to Java6/Feisty.

---

### Post by firebadger on 2007-06-07
You need to open up your java control panel and change a configuration option.  You'll find it somewhere like this.. /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel.  The option you need to change is under the advanced tab and you should uncheck the "Check publisher certificate for revocation" option.

---

### Post by Hikaru79 on 2007-06-07
> **firebadger said:**
> You need to open up your java control panel and change a configuration option.  You'll find it somewhere like this.. /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel.  The option you need to change is under the advanced tab and you should uncheck the "Check publisher certificate for revocation" option.

Hm, I just went and checked that. It turns out, it was already unchecked :( Any other ideas?

---

### Post by firebadger on 2007-06-08
Not off the top of my head.  Are you sure that the Control Panel you ran was for the JRE your plugin is using?

---

### Post by Hikaru79 on 2007-06-08
> **firebadger said:**
> Not off the top of my head.  Are you sure that the Control Panel you ran was for the JRE your plugin is using?

Yup, I checked. Also, I've tried running it with ```
javaws /path/to/jnlp/file
``` also, and the same thing happened (and I checked the version string of the javaws to make sure it really did point to Sun Java 6.)
Thanks, by the way, for your continued patience :)

---

