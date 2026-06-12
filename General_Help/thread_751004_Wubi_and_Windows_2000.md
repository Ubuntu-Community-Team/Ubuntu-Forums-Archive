---
title: "Wubi and Windows 2000"
date: 2008-04-10
forum: General Help
---

### Post by w3stfa11 on 2008-04-10
Does anyone have any experience using Wubi with Windows 2000? I read that it's supported and should work, but perhaps it hasn't gotten the same amount of testing as WinXP and Vista. 

Well, I'm going to give it a shot once 8.04 Final arrives using Xubuntu. I'll post here my results. :)

---

### Post by ago on 2008-04-10
Well in fact if you have w2000 some testing would be appreciated, particularly before final.

---

### Post by w3stfa11 on 2008-04-12
Well, Wubi worked fine and it installed Xubuntu successfully. Unfortunately, Xubuntu couldn't recognize my keyboard. It was a corded Logitech keyboard but (I think) it thought it was a wireless Microsoft keyboard. So, when I was brought to the login screen, I couldn't enter my login information.

---

### Post by ago on 2008-04-13
w3stfa11

The issue with the keyboard was that your keys did not print the right chars (layout mismatch)? Or was it that your keyboard would not work at all?

In the first case please file a report in [https://bugs.launchpad.net/wubi/+bug/188492](https://bugs.launchpad.net/wubi/+bug/188492) 

I was also told that with W2000 wubi appears in add/remove programs. Could you pls check that and post your experience here: [https://bugs.launchpad.net/wubi/+bug/204346](https://bugs.launchpad.net/wubi/+bug/204346)

---

### Post by w3stfa11 on 2008-04-14
It was the latter. No matter what key I pressed, it wouldn't work. I think I've had this problem before with another distro, so I don't think it's Wubi's fault.

I do remember uninstalling using Add/Remove and it uninstalled fine.

---

