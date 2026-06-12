---
title: "Open with Wine"
date: 2018-01-18
forum: General Help
---

### Post by heroquestelf on 2018-01-18
Hey guys,

First off, I am running a Dell Experion with a 4x Intel Core i5-4460 3.2  GHz  processor with 8088MB of RAM. My Distribution is Ubuntu MATE  16.04.3  LTS.

I am going to ask a question that I'm 95% certain I already know the answer to. It starts with the fact that one of my all time favorite Windows programs is a Image viewer called Irfanview. It's really a fantastic little piece of software.

When I was running Windows, this is the software I used as my default viewer for images.

Now, the software will successfully install using Wine, and it works great, but I am assuming there is no way to make Ubuntu use Irfanview as the default image viewer. Am I correct?

---

### Post by raleigh3 on 2018-01-18
I don't think you can set it as default image editor because Irfanview is being run by an emulator.

I recommend Gimp or KolourPaint.

---

### Post by DuckHook on 2018-01-19
I don't want to hold out false hopes, but:

[LIST]
[*]Absolutely ancient thread about exactly this issue. There's not a snowball's chance you will get this exact process to work, but it can lay out the general strategy and point you in the right direction: [https://ubuntuforums.org/showthread.php?t=1250355](https://ubuntuforums.org/showthread.php?t=1250355)
[*]Another six-year-old thread teaching how to define a Windows app as a MIME type. Once a MIME type is defined, you can theoretically associate whatever file types you want to that app: [https://askubuntu.com/questions/224017/changing-the-default-program-for-an-application](https://askubuntu.com/questions/224017/changing-the-default-program-for-an-application)
[*]Finally, a thread posted just yesterday in which a fellow forum member worked around a bug in the latest WINE/Ubuntu combo that restricts the apps that can be invoked with WINE. You may not need this last functionality, but it is useful to look at this member's solution for its techniques: [https://ubuntuforums.org/showthread.php?t=2382617](https://ubuntuforums.org/showthread.php?t=2382617)
[/LIST]
As to how all of it goes together, you will need a better man than I to help you there, Gunga Din.

---

### Post by Matt_Boling on 2018-01-19
Have you considered Okular?
<snip>

---

### Post by QIII on 2018-01-19
The OP is asking how to make Irfanview the default image viewer.  They are not asking for suggestions for alternative native Linux applications.

Please stay on topic.  DuckHook has provided a spot-on example of how to do that.

---

