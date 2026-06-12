---
title: "Can't be this difficult to install JRE"
date: 2007-07-21
forum: General Help
---

### Post by ed67 on 2007-07-21
Firefox wants java to load certain pages.  I'm using ubuntu 7.04, and at one time I installed JRE through synaptic I think, but had to reinstall ubuntu and now I can't seem to locate it in synaptic.

Is there a repository I haven't enabled maybe?  I just can't remember what I did and can't find anything here other than long command line instructions.  I will revert to that if I have to but.........  

Also, which type would I download from Sun's website if it comes to that?  There's Linux RPM, Linux self extracting, etc.  Idk what any of it means really.

---

### Post by Saner on 2007-07-21
Try

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

Although I didnt install 6 I installed 1.5 cause 6 seems to refuse to work with my online poker :D

---

### Post by Sef on 2007-08-19
Applications > Add/Remove > Show: All Available Applications > in the Search box: Sun Java 6 > Check Sun Java 6 Web Start > Click  OK > Click OK again

---

### Post by ed67 on 2007-08-19
Yes, I've found and installed JRE but it still doesn't work.  I read somewhere that I have to create a "symbolic link".  How do you know where JRE was installed to go to that directory?  Why do all the other Firefox plugins install and work fine but JRE doesn't?

---

### Post by thevictor390 on 2007-08-19
Heres what happened to me on the PPC version, anyway:

The plugin in Firefox linked to the JDK, not the JRE which I had.  I t showed a a broken link.

The fix:

navigate to the /usr/lib/firefox/plugins directory in terminal

sudo rm <name of plugin that's broken>
sudo ln -s /usr/lib/jre1.5-ibm/jre/bin/mozillaplugin_oji.so
                                            ^ this will change since you didn;t have to get the IBM PPC port.  See if you can find the right plugin based on the broken link in the plugins folder (if that's even your problem).

---

