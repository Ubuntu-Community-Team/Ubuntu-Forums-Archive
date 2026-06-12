---
title: "eclipse takes a long time to start and freezes"
date: 2007-01-31
forum: General Help
---

### Post by strycore on 2007-01-31
Eclipse has been acting weirdly since a few days , it takes about 5 minutes to start and it freeze for 2 minutes each time it uses the auto completion .
When it occurs the JVM (i use sun-java5-jre) takes 100% cpu

i don't have this problem if i start eclipse with another user or root

i tried to : 
-uninstall all the plugins
-uninstall and reinstall eclipse and sun-java5-jre
-delete the ~/.eclipse directory
-use another version of eclipse (wtp-all-in-one-sdk-R-1.5.2-200610261841-linux-gtk)

it didn't change anything , i still have the same problem 
I would be very thankful for any help :)

---

### Post by mcglnx on 2007-01-31
- Any message on the console? (using XTerm?)
- Did you try to install JDK and Eclipse by yourself? It is straight forward normally and you come with a clean install. I've never liked other's packaging - does not work most of the time.

---

### Post by strycore on 2007-01-31
if i run eclipse from the console i have the following message : 

```
 testing /usr/lib/jvm/java-gcj...not found
  testing /usr/lib/kaffe/pthreads...not found
  testing /usr/lib/jvm/java-1.5.0-sun...found

```
and then nothin happens

someone on IRC told me to search for the JVM pid's and do kill -3 <pid>

here the result of that : [http://paste.ubuntu-nl.org/3626/](http://paste.ubuntu-nl.org/3626/)

Eclipse packages work well on my laptop and with a testing user account so i think the problem i caused by a misconfiguration of java in my home directory

---

### Post by mcglnx on 2007-01-31
I never use Kaffe. 
Did you try with Sun's JDK? It's free now.

---

### Post by strycore on 2007-01-31
i don't use kaffe or gcj , i only have the sun-java5-jre package installed
(i worked fine a few days ago ...)

---

### Post by mcglnx on 2007-01-31
> **strycore said:**
> (i worked fine a few days ago ...)
So comes to me other questions:

- What did you change since 'few days ago'?
- What about re-installing Eclipse, then if does not work, Java?

---

### Post by strycore on 2007-01-31
the problem i solved , i don't know really how but now it works

i replaced the sun-java5-jre with j2se 1.4 (the one i'm using on my laptop) , but it didn't do anything

i moved every hidden directory from my home dir in  a temp dir , restarted the session and put the dirs back , i lost my theme configuration , gnome config ... but now Eclipse starts just fine and does not freeze :D 

It took me 5 minutes to put my gnome settings back and now i'm happy :)

---

### Post by phossal on 2007-01-31
A lot of things use Java. And a lot of things interact with, and mess with, the default JVM. Beryl, though people love it, causes all kinds of problems as an example. 

One of the ways I've gotten around it is manually installing eclipse and a separate version of the JDK. They play nicely together in isolation.

You can refer to my sig for details. lol If you're already happy with your existing setup. Ignore me. ;)

---

### Post by strycore on 2007-01-31
i'm using beryl , maybe it's what messed up my java config

---

### Post by phossal on 2007-01-31
lol   ;)

I figured. I hate beryl, but it seems to get a lot of attention. It's like a hot chick who is really stupid. Big pain the butt, virtually useless, but guys dig 'em anyway.

---

### Post by mcglnx on 2007-02-03
lol ;)

---

### Post by rattusdatorum on 2007-03-02
I have the same problem, just out of nowhere I can't start eclipse anymore.
There should be an other way then reinstalling the whole thing.

---

### Post by phossal on 2007-03-02
> **rattusdatorum said:**
> I have the same problem, just out of nowhere I can't start eclipse anymore.
**There should be an other way then reinstalling the whole thing**.

There is, of course. It's an opportunity cost though. It takes 5 minutes to show a guy how to download the things manually - because there are virtually no roadblocks. It could take hours or more to diagnose a package, or mixed, install failure. I've never had a manual install stop working, but I've had it happen with packages. Who wants to support that? If you don't understand your system well enough to figure it out yourself, you might benefit from a simpler approach.

---

### Post by strycore on 2007-03-02
doing a manual install did not solve anything for me.
rattusdatorum, did you try launching Eclipse on a clean session ?
if it works fine here then it's the same type of problem I had

---

### Post by phossal on 2007-03-02
> **strycore said:**
> doing a manual install did not solve anything for me.
Manually installing both the JDK and eclipse isn't supposed to *solve* any problems - except that of performance. When you download a packaged version of eclipse, it installs it in such a way that diagnosing *why* it won't start is 100% more complicated. Manually installing the JDK and eclipse removes many of those obstacles, which makes it easier to *support and diagnose*, among the *other* reasons for being the smarter way. I understand eclipse, Java, and Ubuntu well enough to figure out *why* your packaged (or mixed) installs stop working - *but who has the time for that?*. Beryl, of course, makes a *huge* difference, too. It's widely known that Java fails while running Beryl. There are hundreds of threads on it. The fix that was common while using JDK 5 was supposedly unnecessary with JDK6, for what it's worth.

---

