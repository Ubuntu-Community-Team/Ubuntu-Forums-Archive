---
title: "get errors installing java6"
date: 2007-05-01
forum: General Help
---

### Post by nick623 on 2007-05-01
I'm using Feisty and when I try to install java and the java plugin using this command:
"sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts"

I get the following error:

Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
subprocess post-installation script returned error exit status 127
Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.

dpkg: dependency problems prevent configuration of sun-java6-plugin:
sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sun-java6-bin
sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java6-plugin:
sun-java6-plugin depends on sun-java6-bin (= 6-00-2ubuntu2); however:
Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
sun-java6-bin
sun-java6-plugin


And now when ever I try to install anything else I get error messages about java and it quits.

Any ideas?

---

### Post by rsambuca on 2007-05-01
Make sure you have the multiverse repositories enabled.  Then I would just use Synaptic and there shouldn't be any problems.

---

### Post by nick623 on 2007-05-01
Enabled the multiverse repos used synaptic. Still get same error message.
Never had this problem with Edgy.

Any input appreciated.

---

### Post by fakie_flip on 2007-05-02
Have you tried installing the package libjline-java?

---

### Post by nick623 on 2007-05-02
> **fakie_flip said:**
> Have you tried installing the package libjline-java?

Where do I get it. I tried "sudo aptitude install libjline-java" and got nothing. 
Shouldn't any libraries be already installed?
I'm confused.

---

### Post by zvacet on 2007-05-03
Just install it from synaptic.

---

### Post by fakie_flip on 2007-05-03
Another guy tried this already. It didn't help. This is a bug in Feisty. You need to report it to Launchpad if you want it to get fixed. That will help everyone out if you do. The developers need to know about this, so they can release a bug fix in the updates.

---

### Post by rsambuca on 2007-05-03
I have java installed with no problems.  Can you please post your /etc/apt/sources.list so we can have a look?

---

### Post by fakie_flip on 2007-05-04
I never thought of that. He could be getting java6 from a bad third party repo that is unsupported by Ubuntu.

---

