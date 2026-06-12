---
title: "NetBeans frequently crashes"
date: 2008-06-18
forum: General Help
---

### Post by Hunterjelly on 2008-06-18
Whenever I run NetBeans 3 basics things happen:

1. It will crash, taking my work with it (usually happens within 5 min. of opening)
2. It will run sluggishly for a while. Then either crashes, or:
3. Runs pefectly (then eventually crashes)

I don't think I have either closed NetBeans before, as it always crashes and I give up using it. So, today is the day I want to try and fix NetBeans. Does anybody have an suggestions?

Thanks in advance.

---

### Post by jamesstansell on 2008-06-19
[LIST]
[*]How did you install NetBeans?
[*]How did you install the JDK?
[*]Are you running Ubuntu 8.04 (Hardy Heron)?
[/LIST]

---

### Post by Hunterjelly on 2008-06-19
I installed NetBeans through 'Add/Remove...' in the Applications menu.

I'm not sure how I got the JDK... If you can tell me what to look for in Synaptic, I'll see if I even have the right one. (looks like I have 'openjdk-6-jdk, should I grab the sun one? If so, how do I set NetBeans to use the proper one?)

Yes, I am running Ubuntu 8.04.

---

### Post by jamesstansell on 2008-06-19
Yes, installing the sun-java6-jdk package is worth trying out.

You may need to run this after installing it.
```
$ sudo update-java-alternatives -s java-6-sun
```

I'm not sure if that will let your netbeans pick up the new JDK or not.  (I don't have netbeans installed from the repository, so can't try it out.)

Beside these forums, launchpad is another good resource for you - both the bugs and answers sections.

(And if you use the Java applet I would suggest that you verify that it still works for you.)

---

### Post by Hunterjelly on 2008-06-19
> **jamesstansell said:**
> Yes, installing the sun-java6-jdk package is worth trying out.

You may need to run this after installing it.
```
$ sudo update-java-alternatives -s java-6-sun
```I'm not sure if that will let your netbeans pick up the new JDK or not.  (I don't have netbeans installed from the repository, so can't try it out.)

Beside these forums, launchpad is another good resource for you - both the bugs and answers sections.

(And if you use the Java applet I would suggest that you verify that it still works for you.)

This appears to have worked, but it broke the program I was working on. No biggie, I didn't get much of anywhere on it anyway.

Thanks for the help, let's hope it keeps working:guitar:

---

