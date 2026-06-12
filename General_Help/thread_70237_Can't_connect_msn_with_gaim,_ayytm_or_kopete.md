---
title: "Can't connect msn with gaim, ayytm or kopete"
date: 2005-09-29
forum: General Help
---

### Post by nkemer on 2005-09-29
i can not connect msn network with any of my messenger clients.:confused: icq and yahoo are ok.
any suggestions?
thank you

---

### Post by Hairy_Palms on 2005-09-29
have u got the screen name and alias the wrong way round? i know ive done that before, should be like the screenshot [IMG]http://i21.photobucket.com/albums/b264/Hairy_Palms/example.jpg[/IMG]

---

### Post by nkemer on 2005-09-29
my setting r just like you.
here is the error message
[ATTACH]2632[/ATTACH]

---

### Post by Zotova on 2005-09-29
Have you been able to connect to msn in the past or have you recently installed ubuntu and you haven't been able to connect from the start?

Also, do you have a firewall/installed one recently? Or do you have a router which has a firewall which could be blocking the port msn uses. Does it help if you try to connect to msn on a different port?

---

### Post by nkemer on 2005-09-29
[QUOTE=Zotova]Have you been able to connect to msn in the past or have you recently installed ubuntu and you haven't been able to connect from the start?[/QUOTE]
i never connect msn since ubuntu installed, i installed ubuntu last week.(by the way, i'm using windows internet connection sharing for access to internet)

---

### Post by Zotova on 2005-09-29
Have you tried ticking the 'Use HTTP Method' box?

This is a screenshot of gaim btw.

[IMG]http://www.shanghai.me.uk/linux/gaimscreen.jpg[/IMG]

Failing that try changing the port to 80

---

### Post by nkemer on 2005-09-29
i tried all you said but , but same result.
thank u anyway,
i think this is not a gaim issue. i see that "port 1863" is closed, and i dont any clue how to open.

---

### Post by Hairy_Palms on 2005-09-29
you could change gaim to a port that you know is open,

---

### Post by Zotova on 2005-09-29
Is the windows machine setup correctly? Is the internet sharing on the other computer blocking msn or something silly like that?

Also, do you dual boot with your computer - can you connect to msn on this computer in windows via the windows pc that shares the internet? If so then we can rule out my first question.

Failing that try something more msn based, amsn for example.

---

### Post by nkemer on 2005-09-29
yes i have dual boot and everything's ok when boot with windows.and i realized a weird thing that i can not connect some web sites too.(ex mail.yahoo.com, real.com)
(amsn behave like others)

---

### Post by nkemer on 2005-09-29
ok. it's solved. it's a mtu size issue.
solution can be find [here]("http://ubuntuforums.org/showthread.php?t=3985&highlight=mtu+size")

---

### Post by Her Ghost on 2008-01-18
@nkemer

I'm glad you found a solution.

Can you explain what you needed to do?  I have read the post you linked to, which talked about modifying the MTU, but what do I need to modify my MTU to?  Also, how would I find out what it currently is?

Thanks

---

### Post by Her Ghost on 2008-01-19
Ok, this is beyond a joke.

I will pay someone real money to fix this, if that's what it takes.

Why does every other computer on my network connect to MSN correctly, but Kubuntu will not?

I have tried changing the MTU and nothing changes.  I have tried Kopete, GAIM, pidgin, aMSN and none of them fare any better than the rest.

I simply want to use MSN, why is this such a big deal?

---

