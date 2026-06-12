---
title: "possible to use both oracle java and openjdk, eg for different users???"
date: 2014-07-09
forum: General Help
---

### Post by a-you on 2014-07-09
Anybody know if it's possible to use java 7 from oracle for one user and openjdk for another??

Or alternately, is it possible to use oracle's java for a java app but to have firefox use the java plugin from openjdk?

Thanks in advance. Btw I wasn't sure where to ask this, hopefully it's not in the wrong place (sorry if it is).

---

### Post by slickymaster on 2014-07-09
Using **update-alternatives** you can manage more than a jdk on the same system, choosing which one you want to use as the main one. Please refer to [Choosing the default Java to use]("https://help.ubuntu.com/community/Java#Choosing_the_default_Java_to_use").

---

### Post by a-you on 2014-07-09
I probably didn't phrase the question very well, because I realize that I can choose between installed versions. The situation I'm in is that one java app I have demands the oracle java but I'm thinking that probably there's going to be better apparmor support for openjdk. If I can have both installed (I do) and then somehow point that one app to the oracle java while still otherwise having the rest of the system consider openjdk as the java to use (especially firefox) then that would be ideal.

I had an idea after posting the question, which was that since I might (???) have to re-install this one java app that refuses to work with openjdk anyway, maybe I could set oracle's java as the version used by the system generally, as slikymaster's link describes, re-install that app, then change the configuration such that openjdk is the version used.

But anyway rephrasing my question: considering what I'm trying to do, if anybody has advice re trying to use oracle's for one app but openjdk for everything else, please let me know (thanks).

I'll come back and mark it as "solved" when I have a chance to try it, then I can add maybe some info about what happened.

---

### Post by a-you on 2014-07-10
bumping if I may...

Just that I'm no expert in the inner workings of a distro, and I don't know how to go about figuring out whether there are problems with having both javas be in use, maybe problems that wouldn't be overt but would still ripple though somehow. Anyway any expert opinions would be appreciated... (thanks again).

---

### Post by slickymaster on 2014-07-10
> **a-you said:**
> bumping if I may...

Just that I'm no expert in the inner workings of a distro, and I don't know how to go about figuring out whether there are problems with having both javas be in use, maybe problems that wouldn't be overt but would still ripple though somehow. Anyway any expert opinions would be appreciated... (thanks again).

Theoretically I would say that there shouldn't be any problems, but I never tested it before. I did found [this]("http://www.if-not-true-then-false.com/2010/install-sun-oracle-java-jdk-jre-7-on-fedora-centos-red-hat-rhel/") where you have OpenJDK and Sun/Oracle Java JDK/JRE 6 and 7 versions installed simultaneously in a Fedora 19 box.

[ATTACH=CONFIG]254609[/ATTACH]

---

### Post by a-you on 2014-07-11
It looks like since installing both and then switching between them isn't problematic, that another approach would be to simply create a launcher that would change the "alternatives" setting anytime I wanted to use that one app that insists on having oracle's version, but switch it back for general use. Also I found this, which might be of interest to anybody else that's wondering about any of this. The fix by [Dude4Linux]("http://askubuntu.com/users/180519/dude4linux") is interesting.

[http://askubuntu.com/questions/323046/troubleshooting-oracle-java-7-with-firefox](http://askubuntu.com/questions/323046/troubleshooting-oracle-java-7-with-firefox)

I did that but when I then tried to reload the profile with

```
 sudo apparmor_parser -r 
```

there was an error message about a line that was totally unrelated to the change. I just don't know enough about apparmor, but it occurred to me that *maybe* that error had to do with the fact that the profile being parsed was one that was meant to be loaded as a secondary thing(?), that is, loaded for java run as a plugin to firefox??


And thanks for that link. I hadn't realized before that this was an issue:

"Add *JAVA_HOME* environment variable to **/etc/profile** file or **$HOME/.bash_profile** file"

---

### Post by a-you on 2014-07-11
This is looking to be more complicated (in ways that I don't understand) than I thought. So I ended up uninstalling openJDK and just using oracle's jave since everything works with that.

In order to try to address the question of apparmor support I've modified the apparmor profile per [Dude4Linux]("http://askubuntu.com/users/180519/dude4linux")'s tip. Whether apparmor is still working or not I don't know ;-) but I expect it probably is. It looks like his tip is only updating the profile to take into account that java has "oracle" in its name, like it could have "sun" in its name before.

---

