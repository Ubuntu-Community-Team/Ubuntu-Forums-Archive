---
title: "require honest answer regarding java"
date: 2005-04-14
forum: General Help
---

### Post by kcy29581 on 2005-04-14
Hi all,

My question is this: Is there any way to install Java on a Ubuntu (5.04) system GRAPHICALLY? The reason I ask: I am very good with computers, can install java in all the commandline methods. Yet I am trying to get my family/friends to see that Linux is a good alternative for them, and they are not that good with software. If there isn't a GUI, they can't use it. They all need Java, so if I say " you need the commandline", the immediate response will be, "Windows can do it..." and they will not give Linux a chance.

I have used Blackdown Java in previous distributions, but I could not find it in Ubuntu. (yes, I enabled universe and multiverse) All the support shows methods where you have to use the commandline, as explained above, not suitable.

Please , if you know how to do this, I will thank you forever! Everything else in Ubuntu works "out of the box" so why not Java? I understand about licensing issues, but last time I checked, Blackdown was "free"?

Also, is Blackdown the ONLY Open Source Java alternative? I have heard about Kaffe but never tried it. A friend even told me that it's not even normal Java in the JRE/JDK sense...

Debian people also have given me no help regarding my question about a "free" Java implementation. All I got was RTFM, and I have RTFM!

Thanks

---

### Post by Bob D. on 2005-04-14
I think jdong has got you covered, mate. The JRE is already in the Backport Projects hoary-extras-restricted repo. Take a look at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/). The actual deb is [here](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/) , but it is easier just to add the backports repos to your sources.list file.

Bob

---

### Post by kcy29581 on 2005-04-14
Thanks Bob D! That's great info :)

May I ask how you found out about that though? I've been looking myself and couldn't find it.

Also, do you have any idea why Ubuntu doesn't have Blackdown or similar in their repositories?

Thanks again!

---

### Post by Bob D. on 2005-04-15
How I found out? Why, by hanging out at UbuntuForums!  ;-)

Really close to the truth though, I'm pretty sure I saw a request for Java the other day and another post saying it was now available.

You can learn more good stuff hanging around here....great community!

Bob

---

### Post by nocturn on 2005-04-15
[QUOTE=kcy29581]Thanks Bob D! That's great info :)

May I ask how you found out about that though? I've been looking myself and couldn't find it.

Also, do you have any idea why Ubuntu doesn't have Blackdown or similar in their repositories?

Thanks again![/QUOTE]

Ubuntu does not redistribute Java because of license issues.
Basicly, Java is free to use, but redistribution is subject to an EULA, which requires that you do not ship any packages that could replace any of the components of the standard Java.   This  is a big restrictions for a Free Software distribution which also offers kaffe, a Free version of Java.

---

### Post by kcy29581 on 2005-04-16
nocturn,

thanks for the info. I didn't realise that EVERY Java implementation was subject to the EULA... That's real nasty. I have always wondered why Sun with all their "we love Linux & Open Source" attitude, still have a thing about licensing Java.

Here's to hoping...

---

### Post by az on 2005-04-16
Sun is either very conservative or very confused when it comes to open source.  I think if they can find a way to make something look like it is open ource, but not really be, they would do it.

---

### Post by easy_target on 2005-08-01
Has anyone tried kaffe? Does it compare?

---

