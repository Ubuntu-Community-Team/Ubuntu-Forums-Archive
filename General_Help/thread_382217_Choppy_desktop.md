---
title: "Choppy desktop"
date: 2007-03-11
forum: General Help
---

### Post by Achenar on 2007-03-11
Hi,
I was using dapper, but after a kernel upgrade something went wrong with my ATI drivers and they stopped to work (X server wouldn't start and display a black screen). Eventually I upgraded to edgy and stopped trying to make the latest ATI drivers work and reverted to xorg-driver-fglrx available in the repositories. (By the way, I used envy and it changed something in my config which allowed direct rendering to work with that package).
My problem now is that the whole system has a choppy response. Graphics, audio, keyboard and I don't know how what's causing it and how to fix this. Any ideas?

Thanks in advance.

---

### Post by Achenar on 2007-03-11
Additional info:
It seems that my CPU goes to 100% periodically and that's what causes the 'choppyness'. I don't know why still...

---

### Post by Achenar on 2007-03-11
I solved the problem. It was gkrellm which was causing it. Could someone suggest another similar program that I may use?

---

### Post by Ek0nomik on 2007-03-11
Uhm, some people use Conky to get that sort of stuff running.  I don't know if it comes with Conky or you need to configure it.  It looks pretty nonetheless.

---

### Post by freerick on 2007-03-13
I have the same problem. I have two Nvidia 6200 cards, and three monitors with Xinerama. 2D rendering is extremely slow but 3D is ok. The CPU goes up to 100% to render normal items such as icons and the headers for windows.

---

