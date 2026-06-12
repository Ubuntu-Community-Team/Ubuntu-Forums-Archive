---
title: "Failed to add/activate connection"
date: 2014-03-17
forum: General Help
---

### Post by amjjawad on 2014-03-17
Hi,

One of the most annoying problems I'm having with Lubuntu and [the new users I'm converting from Windows to Linux]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") is this problem (beside of course other issues).

[ATTACH=CONFIG]251221[/ATTACH]

This is very common issue that I have always faced with Lubuntu which I'm not sure it has been addressed correctly in the past or not.

Now, the situation is, the owner of that machine is in France right now and not on the neighbourhood. And of course, there is no internet and no other machine (she is messaging me on Facebook from her phone) so I can't ask her to send me any output to any command :) not to mention, she's new to Linux and all that.

Two reasons to start this thread:

1- Help that user Online.
2- Highlight and address this endless issue on Lubuntu and hopefully fix it once and for all. Yes, I know, that will require a bug report. Can't help in this right now for the mentioned reason above.

I will make sure to send this thread to Lubuntu Team as well. 

Now, any idea how to overcome this?

She did a reboot, log off and log back in. She turned the Networking Off and then back On but nothing happened.

Thoughts?

Help is highly appreciated.

Thank you :)

---

### Post by sysmatck on 2014-03-17
This is a problem to connect to a network? Wired or Wireless?

Maybe opening NetworkManager with root privileges?? Kill all NetworkManager process and open it on lxterminal with $sudo nm-connection-editor

---

### Post by amjjawad on 2014-03-18
> **amjjawad said:**
> Hi,

One of the most annoying problems I'm having with Lubuntu and [the new users I'm converting from Windows to Linux]("http://amjjawad.blogspot.com/2014/01/2014-report-project-convert-my.html") is this problem (beside of course other issues).

[ATTACH=CONFIG]251221[/ATTACH]

This is very common issue that I have always faced with Lubuntu which I'm not sure it has been addressed correctly in the past or not.

Now, the situation is, the owner of that machine is in France right now and not on the neighbourhood. And of course, there is no internet and no other machine (she is messaging me on Facebook from her phone) so I can't ask her to send me any output to any command :) not to mention, she's new to Linux and all that.

Two reasons to start this thread:

1- Help that user Online.


Problem Solved.
User was logging in as 'Guest'.

> 
2- Highlight and address this endless issue on Lubuntu and hopefully fix it once and for all. Yes, I know, that will require a bug report. Can't help in this right now for the mentioned reason above.

I will make sure to send this thread to Lubuntu Team as well. 

I'm following up with Lubuntu Team about this issue. [Julien stated that he has never seen this bug before]("https://lists.ubuntu.com/archives/lubuntu-users/2014-March/006910.html"). Once I'm on a machine with Lubuntu, I will try to produce this bug and then report it. As everyone may know, without a reported bug, nothing will be solved.

So, the issue is not yet solved 100% except for that user.

Thank you!

---

### Post by amjjawad on 2014-04-24
Hi,

Sorry for taking so long to report back. I have [just emailed]("https://lists.ubuntu.com/archives/lubuntu-users/2014-April/007266.html") Lubuntu Team and CC'ed Julien. 

Let's hope something will happen this time :)
It is about the networking issues with Lubuntu in general and the URL of this thread was included.

Thank you!

---

