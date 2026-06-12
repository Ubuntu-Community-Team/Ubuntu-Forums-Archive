---
title: "fglrx and firefox on non-gnome Desktop Managers"
date: 2007-04-12
forum: General Help
---

### Post by Nith on 2007-04-12
Hello,

A little while ago, I installed packages kubuntu-desktop and xubuntu-desktop as well as fluxbox and I found that my Firefox would not run in any of the other desktop managers other than gnome. I hung around several irc channels looking for a solution and no one had a clue, hence why I share this info in this post.

I'm running edgy on an ASUS W1N laptop with an ATI Radeon 9600, and when I first installed ubuntu, I installed the ATI drivers right from ATI's main web site. I followed instructions posted on ubuntuguide and everything appeared to have worked although I never really tested it. (Got beryl + xgl working for a while... that was a fight).

After a particular situation led me to find out that I was not able to do double buffering in openGL, I started investigating. I eventually removed the xorg-driver-fglrx package and the two others installed by ATI's installer and reverting back to mesa. The funny thing is... now that I've done this, Firefox works in other desktop managers.

Just thought some other frustrated user might have come across this same issue and may find some comfort in my answer.

My only real question is will I experience a great loss in performance by using mesa drivers instead of screwing around with getting fglrx installed?

Thanks for answers and I hope this post helps someone.

---

### Post by Kisil on 2007-04-13
I used to have a Radeon 9500, and the performance was about 1/2 as fast with mesa as opposed to fglrx.  Granted that was about a year ago, and the 9500 isn't really mainstream, but there's my 2 cents.

It was always a bear getting fglrx to work, though.

---

