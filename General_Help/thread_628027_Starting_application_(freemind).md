---
title: "Starting application (freemind)"
date: 2007-11-30
forum: General Help
---

### Post by intrader on 2007-11-30
Thanks for the above list. I had already searched for a possible solution.

The problem is that Freemind does no run properly in ubuntu 7.10. I have Googled for a solution that works when I issue the following commands from a terminal:

export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/;export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.03/bin/;freemind

(all in one line).
I want to associate the above commands directly to the Freemind icon. If I put the command line in the properties for the application menu entry, the application hangs and must be killed. The Freemind desktop comes up without its menus or icons

:confused:

Thank you

---

### Post by intrader on 2007-12-03
I have figured out. 

I changed the freemind menu command property to point to a bash shell file in /usr/local/sbin/ in file 'Launch freemind'. I then changed the file to executable via the chmod 755 command. 

The bash shell file's contents is:

#!/bin/bash
#launch by ./'Launch freemind'
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.03/;export PATH=$PATH:/usr/lib/jvm/java-6-sun-1.6.0.03/bin/;freemind

That opens freemind properly:)

---

### Post by albertogreco on 2008-05-01
Thank you for your trick.
If jre has a different version number the script doesn't run.

It is possible to make the following corrections, that are more general because the directory /usr/lib/jvm/java-6-sun is linked to the right dir.

If I rename the script as lfreemind and put it in PATH, then I will use it from any user.

#!/bin/bash
#launch by ./'Launch freemind'
#or put it in /usr/sbin and launch it without starting dot-slash
export JAVA_HOME=/usr/lib/jvm/java-6-sun/;export PATH=$PATH:/usr/lib/jvm/java-6-sun/bin/;/usr/bin/freemind
:KS

---

### Post by finchmatt on 2008-05-07
thanks All, this fixes my screen size problem.

I have been trying to fix this for some time.

---

### Post by GregA on 2008-05-11
Just installed (updated to Hardy).  Now I see FreeMind .9-b17 won't run.  I'm not a developer or techie, but I'm assuming Hardy has a newer version of Java, and perhaps it's not at the former location.

Will the script described in this thread fix (launch) FreeMind?  I can visualize how to move that script to /usr/local/sbin using Konqueror (as Super User), but how do copy and paste that script in Gnome & Nautilus?  Sorry for the dumb newbie question, I'm not sure of myself in Gnome yet.   Is there another way to run FreeMind.  Can I downgrade to Java 5?   I know at our workplace, all that's required to run FreeMind is JRE 1.4 or later. 

Thanks for any basic info/help.

---

