---
title: "One problem in Firefox and two in Opera"
date: 2008-04-27
forum: General Help
---

### Post by diplomat.x on 2008-04-27
Hi,

Iam on ubuntu 8.04.

Firefox:

I sometime connect to the internet using my cellphone. i.e EDGE. Firefox works with ADSL modem but doesnt work when i connect to internet using my phone. Opera and update manager all work on EDGE so iam 100% on the net.

How do i get firefox to discover the internet?


Opera:

1- I cannot click the scroll button and vroom up and down like in firefox. I can roll up and down using scroll button but i am talking about the fast scroll after u click the middle button.

2- Java doesnt work in opera. Though i have validated the java path, it still doesnt work. The validated java path >> /usr/lib/jvm/java-6-sun/jre/lib/i386

**Finally if some MOD/ADMIN is reading, please see why i am not able to post threads in Absolute Beginner forum?? I dont remember bombing any place so why the barring?... I messaged here yesterday but no reply [http://ubuntuforums.org/sendmessage.php](http://ubuntuforums.org/sendmessage.php)**


Thanks for reading and any help will be appreciated. :)

---

### Post by diplomat.x on 2008-04-27
Okey, solved the firefox problem. Deleted the .mozilla folder from /home and it recognizes now that i am on net.

help me with opera problems.

---

### Post by diplomat.x on 2008-04-28
Well Well, the firefox problem which i thought was solved is still there. I didnt use ADSL modem yet after it worked with my phone internet but it has stopped working again. If i delete .mozilla folder again then it works. But i cant keep deleting my settings, bookmarks, history everyday.....What do i doo.....no one even replies...cmon...

EDIT : I wouldnt be moaning if i had atleast ONE fully functional browser. I would use opera but java doesnt work in it !!
WHAT A PITY, i am FORCED to use Vista just cos no internet browser works in ubuntu....toooooo baaad :mad:

---

### Post by diplomat.x on 2008-04-28
Bumping to top....Mods can ban me if they think i am being too frequent. But this problem gotta go today...So i am gonna bring this at top every hour or so.

---

### Post by TransitMan on 2008-04-28
In Firefox, check your Connection Settings under Preferences -> Advanced -> Network -> Settings.
Make sure that No Proxies is checked. That could be holding you back, as it was checked when I upgraded to HH.

The scroll issue in Opera can be fixed by Enabling Mouse Jestures.

As for the java issue, this is the latest jre that came with HH and is validated correctly by Opera - /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386
You may want to look at it again to make sure you have the correct path.
Also, make sure under Adavanced that the Enable Java is checked.

Now something for you to think about.
You're in India, and I'm in the US. A lot of folks between us are either in bed, getting ready for bed or getting up for work. Getting in the net may be the last thing on their minds.
In order for folks to answer yours or anyone elses questions, it takes time. Sometimes some can come along and give you the right answer right away, and then sometimes it can a day or so.
Have patience, for your questions will be answered eventually, without the badgering.

---

### Post by arm-c on 2008-04-28
Try to remove using synaptic the "OpenJava"  Then install Sun Java.

For some reason, they shipped Open Java and it doesn't work with the java sites I use.  In FF, you should be able to check what it is using by putting in URL  "about : plugins" (no spaces before or after the : _ had to do to prevent the auto smile from appearing.)

Hopefully that fixes your Java issue.  Do a search for my post previously in Upgrades/installation.  Posted it yesterday.  It may be of help for you, cause I spent all day SAT getting back to functional internet.

---

### Post by diplomat.x on 2008-04-28
> **TransitMan said:**
> 

In Firefox, check your Connection Settings under Preferences -> Advanced -> Network -> Settings.
Make sure that No Proxies is checked. That could be holding you back, as it was checked when I upgraded to HH.



"No Proxy" wasnt checked for me by default. Checked it now but it still didnt work. Deleted .mozilla folder from home and restarted firefox>>changed to no proxy again. It works as of now but i am yet to check if it always work after restarting.

> **TransitMan said:**
> 

The scroll issue in Opera can be fixed by Enabling Mouse Jestures.



Mouse gestures were enabled, looked here and there and enabled panning from middle click options.

> **TransitMan said:**
> 
As for the java issue, this is the latest jre that came with HH and is validated correctly by Opera - /usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386
You may want to look at it again to make sure you have the correct path.
Also, make sure under Adavanced that the Enable Java is checked.



Now when i open this site to check  >> [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml) Opera simply crashes. 
Though this site >> [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1)  tells me that recommended java version is installed.


> **TransitMan said:**
> 

Now something for you to think about.
You're in India, and I'm in the US. A lot of folks between us are either in bed, getting ready for bed or getting up for work. Getting in the net may be the last thing on their minds.
In order for folks to answer yours or anyone elses questions, it takes time. Sometimes some can come along and give you the right answer right away, and then sometimes it can a day or so.
Have patience, for your questions will be answered eventually, without the badgering.

Yeah, i agree i was annoying. Dont mind. I had just started my laptop and firefox didnt work and opera wouldnt open my bank's site. Anyways, i apologise for the harsh words. :guitar:

---

### Post by diplomat.x on 2008-04-28
> **arm-c said:**
> Try to remove using synaptic the "OpenJava"  Then install Sun Java.

For some reason, they shipped Open Java and it doesn't work with the java sites I use.  In FF, you should be able to check what it is using by putting in URL  "about : plugins" (no spaces before or after the : _ had to do to prevent the auto smile from appearing.)

Hopefully that fixes your Java issue.  Do a search for my post previously in Upgrades/installation.  Posted it yesterday.  It may be of help for you, cause I spent all day SAT getting back to functional internet.

"OpenJava" doesnt exist in my synaptic. :confused:
But anyways, i have sun java installed already.

---

### Post by arm-c on 2008-04-28
I am sorry.  The actual name of the package is:

openjdk-6-jre and associated packages.

Install

sun-java6-jre
sun-java6-plugin

Those should work.

In firefox... you can see what Java you are using by typing in the address bar:  

about:plugins

Scroll down and see what Java plugin you have.  It is using the OpenJDK if it says "icetea" or something to that effect.

What I see now that I uninstalled the OpenJDK is the following:

Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

Hope that helps... let me know.

---

### Post by diplomat.x on 2008-04-29
sun-java6-jre was installed. I have installed sun-java6-plugin and opera ROCKS !! 
Thanks a ton arm-c. Now i have one complete browser. 

About firefox, java works in it but the problem is that its hell bent on working only when i am on ADSL internet and not when i am on EDGE network. I have to delete .mozilla folder from home everytime i start ubuntu for firefox to discover my mobile internet.

---

### Post by ucro on 2008-06-13
I had the exact same problem with opera, java was installed, worked in firefox but not in opera, the thing was that opera validated the path:
[SIZE="3"][COLOR="Red"]/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386[/COLOR][/SIZE]

but it still didn't work.

I read some threads from other linux forums with the same problem too, couln't find the solution.

Anyways, picking through the system i noticed a [SIZE="3"][COLOR="Red"]"/usr/java"[/COLOR][/SIZE] file, in there a [SIZE="3"][COLOR="Red"]"/usr/java/jre1.6.0_06/lib/i386"[/COLOR][/SIZE] file also exists, so tried that in opera and it validated the path, and that solved my problem.

Hope is usefull to someone.:lolflag:




[SIZE="3"][COLOR="Red"]"/usr/java/jre1.6.0_06/lib/i386"[/COLOR][/SIZE]

---

