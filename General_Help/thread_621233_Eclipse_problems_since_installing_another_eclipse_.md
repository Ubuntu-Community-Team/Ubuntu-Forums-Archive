---
title: "Eclipse problems since installing another eclipse based product (Intalio designer)"
date: 2007-11-23
forum: General Help
---

### Post by mylesorme on 2007-11-23
I had successfully installed eclipse simply using applications > and so on.

I then tried to install a product called Intalio Designer that is based on eclipse. It comes as an archive that you extract and then run the eclipse from where it is extracted.

It had errors loading views, so I uninstalled my usual eclipse to see if that was a problem. It wasn't .

Now I have deleted directory with Intalio designer and reinstalled Eclipse - It doesn't load - I get the splash screen, then it goes away. usr/local/lib/eclipse/features and plugins are empty.

if I type eclipse in the terminal I get the following...

searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-6-sun...found
Could not create /usr/local/lib/eclipse/.eclipseextension. Please run as root:
    touch /usr/local/lib/eclipse/.eclipseextension
    chmod 2775 /usr/local/lib/eclipse/.eclipseextension
    chown root:staff /usr/local/lib/eclipse/.eclipseextension

If I type sudo followed by the commands listed above nothing much happens...

Can anyone give any pointers please? I'd like to get eclipse back so that I can try some other BPMN tools

---

