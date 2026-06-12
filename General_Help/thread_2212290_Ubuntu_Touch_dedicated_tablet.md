---
title: "Ubuntu Touch dedicated tablet"
date: 2014-03-20
forum: General Help
---

### Post by lawrence3 on 2014-03-20
[SIZE=4]**The case**[/SIZE]

I need to make an architectural decision for developing (actually porting) my embedded solution. I am investigating the options to use Ubuntu Touch on a tablet for this.
Here is the question on SO where I asked to discuss this topic. There you can see the requirements of my system, but the main concerns are:


[LIST]
[*]Dedicated system (minimum amount of other applications running, even in the bg)
[*]Multiple processes, ability to set priorities
[*]Ability to assign a process to a single CPU Core (cpu affinity)
[*]Inter-process communication mechanisms
[*]Complete hardware control (WiFi, 3G, GSM, mic, speaker, display, ...)
[*]Creating sockets, etc.
[/LIST]

**[SIZE=4]The questions[/SIZE]**

From my search, I understand these could be the issues when using Ubuntu Touch as my platform:


[LIST=1]
[*]It uses HTML5 and QML (Qt), which are aimed more towards UI and UX. If I want more control over my processes and the complete system, I would have to go for something "stronger" like Python. But if I don't use Ubuntu SDK, I will have no way to interface the HW in easy way. Can this be overcome some way?
[*]Ubuntu Touch currently doesn't support much devices, and most probably it won't support those devices that will fit my requirements hardware-wise. How much effort would it be to do the porting myself? Would it even be possible, considering that the HW will probably be different?
[*]How hard would it be to implement a dedicated solution using Ubuntu Touch? Can I tweak it to my needs easily? It should be very similar (if not the same in the newer versions) as regular Ubuntu (it's even the same image if I understood correctly)
[*]Maybe some of my initial assumptions are wrong about the topic, if so - please correct my point of view accordingly.
[/LIST]

**[FONT=verdana][SIZE=4]Finally[/SIZE][/FONT]**

Thank you for your time and any help you may offer.

---

### Post by grahammechanical on 2014-03-20
Please allow me to put a hypothetical situation to you. Supposing you were doing this development work on a desktop machine, would ubuntu meet your needs? Could you do what you wish with Ubuntu? I ask this because Ubuntu Touch is Ubuntu. Or will be by the end of this year or maybe the middle of next year.

The first stage for Ubuntu Touch was completed last spring and that was to optimise Ubuntu Touch for the phone form factor. The second stage of Ubuntu Touch is almost complete. And this is to optimise Ubuntu Touch for the tablet form factor. There is a third stage that has only just been started and that is to converge the Ubuntu Touch code base into the Ubuntu Desktop code base so that there is just one code base called Ubuntu. I expect to see the two code bases converged by the release of 14.10 or 15.04 at the latest.

The push towards HTML5 and QML(QT) is for application development. That should not be taken to mean that applications written in other languages will not run on Ubuntu. The development of the Ubuntu SDK (a version of QT creator) is geared towards making it easy for anyone, even those with no experience of developing applications, to produce apps and get them accepted into the Ubuntu software centre. A lot of effort has been taken to protect users from malicious code. Which will also benefit uses of the desktop.

Users of mobile devices like to install apps and the number of apps available can make a difference between a mobile device getting a market share or not. So, that is why development of the SDk is in that particular direction.

As I understand it you are thinking of using Ubuntu Touch as a base for an embedded OS with applications written by yourself in the programming language of your choice. Would you want these applications to be part of the Ubuntu software centre? Perhaps not. So, the present difficulties that developers experience in getting their app accepted in the software centre would not apply to you.

As for devices, the intention is for Ubuntu to be pre-installed on retail mobile devices. But as Ubuntu is open source there is nothing to stop anyone from porting Ubuntu to other devices. And many are doing this.

[https://wiki.ubuntu.com/Touch/Devices](https://wiki.ubuntu.com/Touch/Devices)

The Ubuntu SDK is also a developing project. I have not noticed anything yet about the SDK supporting Python but it may come in the future. This is the latest I could find.

[http://www.jonobacon.org/2014/02/13/forward-momentum-in-the-ubuntu-app-developer-platform/](http://www.jonobacon.org/2014/02/13/forward-momentum-in-the-ubuntu-app-developer-platform/)

As for Python it is in Ubuntu.

[https://wiki.ubuntu.com/Python](https://wiki.ubuntu.com/Python)

I am running 14.04 and it has Python 2.7.5 and Python 3.3 installed.

Regards.

---

### Post by lawrence3 on 2014-03-21
First, thank you for your great answer!

You have made things much clearer for me. I have some more questions though :) Sorry if I'm being ignorant :)

> [COLOR=#000000]Please allow me to put a hypothetical situation to you. Supposing you were doing this development work on a desktop machine, would ubuntu meet your needs? Could you do what you wish with Ubuntu? I ask this because Ubuntu Touch is Ubuntu. Or will be by the end of this year or maybe the middle of next year.
[/COLOR]
[COLOR=#000000]The first stage for Ubuntu Touch was completed last spring and that was to optimise Ubuntu Touch for the phone form factor. The second stage of Ubuntu Touch is almost complete. And this is to optimise Ubuntu Touch for the tablet form factor. There is a third stage that has only just been started and that is to converge the Ubuntu Touch code base into the Ubuntu Desktop code base so that there is just one code base called Ubuntu. I expect to see the two code bases converged by the release of 14.10 or 15.04 at the latest.
[/COLOR]

Ok, this sounds promising. If this is the case, then there will be no difference, except the hardware interfacing.
You say that Python is part of Ubuntu and i know it is, but I am not sure how using python will effect the HW accessing?
It sure would be swell to have access to some API that simplifies HW access. What is (or will be) the common way of doing in Ubuntu? Is there such an API? I guess with this shift towards QML it should be provided via Qt somehow? This would mean i could access it from other languages like Python (PyQt, PySide...)?

For exampe, how would i make a call without SDK, from Python? How would I take a picture, capture microphone input, etc...?

> [COLOR=#000000]As I understand it you are thinking of using Ubuntu Touch as a base for an embedded OS with applications written by yourself in the programming language of your choice. Would you want these applications to be part of the Ubuntu software centre? Perhaps not. So, the present difficulties that developers experience in getting their app accepted in the software centre would not apply to you.[/COLOR]

No, I will not want the applications to be part of the Ubuntu software centre, they will be dedicated embedded system.

> [COLOR=#000000]As for devices, the intention is for Ubuntu to be pre-installed on retail mobile devices. But as Ubuntu is open source there is nothing to stop anyone from porting Ubuntu to other devices.[/COLOR]

This is the part that will most likely be responsible for my final decision.
I know that difficulty of porting depends on the hardware at hand, but what is the common learning curve for someone with no experience in such tasks?

Regards!

---

### Post by lawrence3 on 2014-03-25
Bump...

---

### Post by lawrence3 on 2014-04-01
Well, seems like the topic is exhausted. :) last bump..

---

