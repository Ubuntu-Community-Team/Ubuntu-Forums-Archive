---
title: "Broken images in Firefox"
date: 2013-05-14
forum: General Help
---

### Post by perlon on 2013-05-14
Hi, I've a little issue that I'm experiencing since I installed Ubuntu 13.04 , using Firefox: sometimes images, banners, etc. are displayed "broken", I attach two examples for better understanding. If I refresh the page without cache the image can be displayes correctly, so it's a temporary problem and it happens on random images/sites. It can also happen that it gets "broken" when the page is already loaded, after a while.
On Ubuntu 12.10 never happened and the Firefox version is always the 20, so I suppose it's a Compiz bug, am I right? Anyway I'm not sure at all about it, so I don't know if it's good to fill a bug report on Launchpad... what should I do?
Do anybody experience the same?

---

### Post by 25tom on 2013-05-14
As a check, does this happen if you use another browser, such as Chromium? If not, then the problem would seem to be with Firefox, and I would be tempted to just reinstall Firefox from scratch and see if that solves it.

---

### Post by perlon on 2013-05-14
It's not easy to reproduce, and I rarely use Chromium, so I can't say... when I used it never happened.
Anyway I just tried to start Firefox from terminal and it gives me this error: 
(process:6665): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed

Could it be related?

---

### Post by 25tom on 2013-05-14
I'm not sure... suggestions anyone else? I'd say reinstall Firefox, but maybe someone else out there has a better fix for the problem...?

---

### Post by Impavidus on 2013-05-14
Problems like this are usually caused by graphics driver problems. Often they only show up in the more graphics-rich programs, like web browsers. May be worth checking.

---

### Post by perlon on 2013-05-14
There are no more recent drivers for now... anyway today FF 21 is out, let's install it first.

---

### Post by perlon on 2013-05-15
Ok, FF 21 doesn't solve.

---

### Post by hoodieatpst on 2013-06-30
Hi! Someone has solved this problem?
I have the same on my Ubuntu 13.04/FF22.0

---

### Post by TheOneLifeRider on 2013-07-19
Hi, I have the same problem, same spec as above. Mind you, I had this problem with U12 and FF21

Thanks

Daniel

---

### Post by Ddeeff on 2013-08-07
I thought that I'd post to say that within the last two months or so I have been getting the same issue. I'll test chrome to see if that is also affected

---

### Post by kinggo on 2013-08-10
another one here. On 12.10 I didn't have this issue. I recently reinstalled 13.04 and that didn't help. On chromium all is fine.

edit:
and on manjaro is the same

---

