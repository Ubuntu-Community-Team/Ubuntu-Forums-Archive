---
title: "This is killing me. (Ubunbtu Speaks to me! Literally. . .)"
date: 2013-09-09
forum: General Help
---

### Post by b4ux1t32 on 2013-09-09
SO, I have been using Ubuntu for a very long time. I mean I think the first time I installed Ubuntu was in the 7.x era. As such, I thought I was an Ubuntu master. Apparently not. I was trying to type a Skype message, and something I typed toggled a command. That command made it so that pretty much everything I did on my keyboard made Ubuntu speak out what I typed. Every click I performed in a different window caused my computer to recite *exactly what is done. *That means if I type a letter, it reads it out to me. If I press "left-shift", my computer says "left shift". In an annoying, synthetic voice. When I tried to type in that italic section earlier, trying to correct a typo entailed  entire string of text I was typing to be re-inserted with the rest of the italic words. That might be Ubuntu, and might just be Chrome for Linux. I'm attempting to be as concise as possible, so that corrections to my typos don't screw over the rest of what I type. This is all very annoying and I cant find an option in any settings menu to fix it . Someone help. T.T

More info: When I click most applications, my computer says "Panel". While in an application, clicking causes nothing to happen, but clicking a link causes my compute to read the link allowed ( I think. Some things are read regardless. It also reads aloud my notifications, like when Dropbox updates and tells me how many files have been added.)

This would likely be a very useful feature if I were blind.

So, I did a little bit more digging and found that if I mute the "speech-dispatcher" program in the sound menus, I can get rid of the speech. But trying to find the program that makes those sounds is a different story entirely. My computer isn't going to have a problem running it with other programs, as it's kinda beefy, but I still want to figure out where the hell this crap is coming from so I don't activate it again.

---

### Post by Crusty Old Fart on 2013-09-09
Too funny.
Now, perhaps you've discovered the modern use for twelve pound sledge hammers.

Perhaps you could discover the application that might be responsible for turning your computer into a chatty child.

You can produce a list of all of your installed applications with the following command:
```

dpkg --get-selections >~/filename_of_your_choice

```
Then you can open the file and look around for anything that appears as the likely offender.

If you get really lucky, you might find an application named: stfu that you can run to get some peace back in your life. (just kidding :cool:)

Good Luck,

Crusty

---

### Post by deadflowr on 2013-09-09
You didn't turn speech reader on in universal access in the system settings, did you?
It's part of orca.

---

### Post by b4ux1t32 on 2013-09-09
> **Crusty Old Fart said:**
> Too funny.
Now, perhaps you've discovered the modern use for twelve pound sledge hammers.

Perhaps you could discover the application that might be responsible for turning your computer into a chatty child.

You can produce a list of all of your installed applications with the following command:
```

dpkg --get-selections >~/filename_of_your_choice

```
Then you can open the file and look around for anything that appears as the likely offender.

If you get really lucky, you might find an application named: stfu that you can run to get some peace back in your life. (just kidding :cool:)

Good Luck,

Crusty
> **deadflowr said:**
> You didn't turn speech reader on in universal access in the system settings, did you?
It's part of orca.
This is what happens when you boot up Ubuntu while drunk when used to Windows. I feel like a total fool. I've even worked with Orca in the past with my mom's students.

Thanks guys. I think I'm going to use that sledgehammer to hit myself the next time I think about booting up Ubuntu after having a few drinks. That, or to use it on myself when I try to boot back into Windows tomorrow. I don't even use my computer for what I had Windows installed for anymore.

---

