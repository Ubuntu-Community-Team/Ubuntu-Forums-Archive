---
title: "How do I purge all java related apps?"
date: 2008-05-02
forum: General Help
---

### Post by RazorJack on 2008-05-02
I have sagetv that works on my 8.04 machine, but not on my upgraded from 7.10 to 8.04 machine (which is my HTPC)....

I believe the issue is java (from the logs) and need to purge all java!  I did way back when install tomcat to learn how it works, something called gij, gcj and a few other things.  Is there a simple way to remove (correction: purge) all java?

---

### Post by RazorJack on 2008-05-02
Oh, and if you wanted the error log:

Sat 5/3 0:46:27.566 Error with DB file:java.io.IOException: Invalid DB file, only partially saved., attempting to restore backup.
Sat 5/3 0:46:28.676 No HDHR devices discovered
Sat 5/3 0:46:28.711 detect 3
Sat 5/3 0:46:44.921 Error in MediaServerConnection of :java.io.EOFException
Sat 5/3 0:46:44.922 java.io.EOFException
Sat 5/3 0:46:44.922     at sage.MediaServer$a.a(Unknown Source)
Sat 5/3 0:46:44.922     at sage.MediaServer$a.run(Unknown Source)
Sat 5/3 0:46:44.922     at java.lang.Thread.run(Thread.java:619)
Sat 5/3 0:46:47.422 locale = en
Sat 5/3 0:46:47.850 Error invoking the method for: default:null|Action:"REM Set the global variables for this STV" of java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.850 java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.851     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.a8.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.a8.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.UIManager.run(Unknown Source)
Sat 5/3 0:46:47.851     at sage.UIManager.byte(Unknown Source)
Sat 5/3 0:46:47.851     at sage.bk.a(Unknown Source)
Sat 5/3 0:46:47.851     at sage.bk.access$700(Unknown Source)
Sat 5/3 0:46:47.851     at sage.bk$1.run(Unknown Source)
Sat 5/3 0:46:47.852 Error invoking the method for: default:null|Action:"REM Startup Apache2 since it fails to start at boot -- for Linux system using NAS" of java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.852 java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.852     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.852     at sage.a8.a(Unknown Source)
Sat 5/3 0:46:47.852     at sage.a8.a(Unknown Source)
Sat 5/3 0:46:47.853     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.853     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.853     at sage.e.a(Unknown Source)
Sat 5/3 0:46:47.853     at sage.UIManager.run(Unknown Source)
Sat 5/3 0:46:47.853     at sage.UIManager.byte(Unknown Source)
Sat 5/3 0:46:47.853     at sage.bk.a(Unknown Source)
Sat 5/3 0:46:47.853     at sage.bk.access$700(Unknown Source)
Sat 5/3 0:46:47.853     at sage.bk$1.run(Unknown Source)
Sat 5/3 0:46:47.865 Error evaluating expression for attribute: default:null|Attribute:DisableOutAnim of java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.867 Error evaluating expression for attribute: default:null|Attribute:DontShowBack of java.lang.ArrayIndexOutOfBoundsException: 112
Sat 5/3 0:46:47.868 java.lang.NullPointerException
Sat 5/3 0:46:47.868     at sage.a8.<init>(Unknown Source)
Sat 5/3 0:46:47.869     at sage.a8.<init>(Unknown Source)
Sat 5/3 0:46:47.869     at sage.b2.<init>(Unknown Source)
Sat 5/3 0:46:47.869     at sage.UIManager.run(Unknown Source)
Sat 5/3 0:46:47.869     at sage.UIManager.byte(Unknown Source)
Sat 5/3 0:46:47.869     at sage.bk.a(Unknown Source)
Sat 5/3 0:46:47.869     at sage.bk.access$700(Unknown Source)
Sat 5/3 0:46:47.869     at sage.bk$1.run(Unknown Source)
Sat 5/3 0:46:47.870 java.net.SocketException: Socket closed
Sat 5/3 0:46:47.870     at java.net.SocketInputStream.socketRead0(Native Method)
Sat 5/3 0:46:47.870     at java.net.SocketInputStream.read(SocketInputStream.java:129)
Sat 5/3 0:46:47.870     at java.net.SocketInputStream.read(SocketInputStream.java:182)
Sat 5/3 0:46:47.870     at java.io.FilterInputStream.read(FilterInputStream.java:66)
Sat 5/3 0:46:47.870     at sage.bk$a.run(Unknown Source)
Sat 5/3 0:51:22.336 java.lang.ArrayIndexOutOfBoundsException
Sat 5/3 0:51:22.337     at java.lang.System.arraycopy(Native Method)
Sat 5/3 0:51:22.337     at sage.v.a2(Unknown Source)
Sat 5/3 0:51:22.337     at sage.v.<init>(Unknown Source)
Sat 5/3 0:51:22.337     at sage.bq.if(Unknown Source)
Sat 5/3 0:51:22.337     at sage.SageTV$3.run(Unknown Source)
Sat 5/3 0:51:22.337 Error w/SageTV client connection:java.lang.ArrayIndexOutOfBoundsException

---

### Post by RazorJack on 2008-05-02
Problem with my install.  Reinstalling resolved problem.

---

### Post by Glaxed on 2008-05-02
If you still need a solution;
```

locate sagetv | grep java >> sagetvcrap
loc=""
while [ 1 ]
do
    read loc || break
    rm $loc
done < $sagetvcrap

```

---

### Post by RazorJack on 2008-05-07
Glaxed..... After spending a day with this, I couldn't agree more.

However, I feel the frustration has todo with the fact the proprietary ATI drivers are C-R-A-P.

---

### Post by miwaypet on 2008-05-07
sudo apt-get remove --purge java*

At your own risk, of course.

---

### Post by Glaxed on 2008-05-08
Lol, yeah i guess that would be a lot easier :D - and more satisfying.

I'm sure somebody has already suggested Envy for your ATIproblem, so I don't really have anything to say..

---

