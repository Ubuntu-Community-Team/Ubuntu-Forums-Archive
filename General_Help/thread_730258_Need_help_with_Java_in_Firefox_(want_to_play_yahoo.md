---
title: "Need help with Java in Firefox (want to play yahoo games)"
date: 2008-03-20
forum: General Help
---

### Post by Lacent on 2008-03-20
Ok, I have searched these forums, and tried a bunch of stuff, but cant get java working for my computer. I installed java, both in firefox, and on my computer, and when I enter the apt-get command in the terminal, it says I have all the latest versions. I would like it to work so I can play yahoo games with my friend. When I open their window, it acts like I dont have java, and tells me to go download it. Any help would be appreciated.

---

### Post by Sef on 2008-03-20
which games do you want to play?  Some games use Active X, so they don't work with GNU/Linux.

Does Java work with other sites?

---

### Post by Lacent on 2008-03-20
Well, in particular dominoes. It is an old game, so I'm not sure if it would use Activex or not... And I'm not sure of another site that uses java that I could test it out on...

---

### Post by markharding557 on 2008-03-20
this link below will tell you if java is working and if it is leaking information [http://www.stilllistener.addr.com/checkpoint1/Java/]("http://www.stilllistener.addr.com/checkpoint1/Java/")

---

### Post by El Conquistador on 2008-03-20
what version of ubuntu are you running. also is it 32 or 64 bit. because i remember on my 64-bit laptop i have some java issues within firefox. but it works just fine on my 32-bit desktop. so you might want to consider that.

---

### Post by Talan6400 on 2008-04-26
It seems I am having the same type of issue.  I upgraded to 8.04 last night/this morning, and I can no longer get into yahoo games. It give me:

```
This game cannot be played using your current settings. Please, try the following:

    * Check to make sure that java is enabled in your browser. (learn more)
    * If you do not have java installed you may download it here.
    * To learn more about java support for browsers, visit our help pages.


```

I went to:[http://www.stilllistener.addr.com/checkpoint1/Java/](http://www.stilllistener.addr.com/checkpoint1/Java/)

And by all indication my JAVA is working correctly.  I have tried bot "Java-6-openjdk" as well as "java-6-sun".

Does anyone know if there is an issue with FF3 and Yahoo games?  I know in the past, Yahoo is VERY slow to accept any new browsers (other than IE), so it very well may be their issue, and not a setting with FF3.

Also has anyone run across about:config in FF3?  Mine not in help anymore, and I haven't looked, so I appologize if it is really easy to find, and I'm just being brain dead :)

Thanks!

---

### Post by kelean on 2008-04-26
I have had problems getting java to work with ff3.  I tried to install java with the add/remove.  Some how it installed icedtea and openjdk-jre6.  The sites i went to verify that java was working showed it was,  But when I went to yahoo games or pogo games I kept getting error saying java not installed.

So what I did is go synaptic and completely removed icedtea and openjdk-jre6 completely.  Then I installed the sun-java 6-bin sun-java6-fonts sun-java6-plugin, and sun-java6-jre.  Then I restarted firefox and played yahoo and pogo games with no problems.

Also just type about:config in the address bar to bring it up.

I hope that that helps you, Kelean.

---

### Post by Talan6400 on 2008-04-26
Much Thanks!!  Works splendid now.  #-o

---

### Post by kelean on 2008-04-27
I am glad it did, I have had many issues getting java to work properly with FF3.

---

