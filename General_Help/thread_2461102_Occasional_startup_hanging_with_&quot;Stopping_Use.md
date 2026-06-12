---
title: "Occasional startup hanging with &quot;Stopping User Manager for UID 121&quot;"
date: 2021-04-24
forum: General Help
---

### Post by Dedalo on 2021-04-24
Hi, I didn't know how to title this thread. Everytime I start the system, this screen appears. Some times it kinda freezes there, and I have to reboot the system. I don't know why it appears, I don't know what it is, and I would like to know if it is possible and recommended to disable it. (I have attached a picture of the screen).

---

### Post by DuckHook on 2021-04-24
This looks like part of a typical start process so no need to mess with it. Network Manager is not the problem here. The problematic line appears to be: ```
Stopping User Manager for UID 121
```UID 121 belongs to GDM which is the Gnome Display Manager. This in turn can be due to a number of different causes. A brief web search turned up this: [https://unix.stackexchange.com/questions/426235/how-to-solve-stopping-user-manager-for-uid-121-error-after-installing-nvidia-d](https://unix.stackexchange.com/questions/426235/how-to-solve-stopping-user-manager-for-uid-121-error-after-installing-nvidia-d)

I don't understand what you mean by "kinda freezes", which is somewhat vague and ambiguous. Does it freeze or not? If not, please describe exactly what it does.

Further questions are:
[list=1]
[*]Has it always behaved this way?
[*]Did this problem start cropping up after you installed some driver or service? Especially nVidia driver?
[*]Or after a kernel update?
[*]As implied by above questions, please provide more general history, context and HW specs.
[/list]
BTW, I took the liberty of changing the thread title to something more informative to potential helpers. If you don't like my change, you can change it to something more to your preference by editing your first post using the "Advanced" editor.

---

### Post by Dedalo on 2021-05-24
> **DuckHook said:**
> This looks like part of a typical start process so no need to mess with it. Network Manager is not the problem here. The problematic line appears to be: ```
Stopping User Manager for UID 121
```UID 121 belongs to GDM which is the Gnome Display Manager. This in turn can be due to a number of different causes. A brief web search turned up this: [https://unix.stackexchange.com/questions/426235/how-to-solve-stopping-user-manager-for-uid-121-error-after-installing-nvidia-d](https://unix.stackexchange.com/questions/426235/how-to-solve-stopping-user-manager-for-uid-121-error-after-installing-nvidia-d)

I don't understand what you mean by "kinda freezes", which is somewhat vague and ambiguous. Does it freeze or not? If not, please describe exactly what it does.

Further questions are:
[LIST=1]
[*]Has it always behaved this way?
[*]Did this problem start cropping up after you installed some driver or service? Especially nVidia driver?
[*]Or after a kernel update?
[*]As implied by above questions, please provide more general history, context and HW specs.
[/LIST]
BTW, I took the liberty of changing the thread title to something more informative to potential helpers. If you don't like my change, you can change it to something more to your preference by editing your first post using the "Advanced" editor.

Hi. Thanks for your feedback.

Well, it goes to a black screen, and there is no way to getting out of there, except opening a terminal and reboot. It could be nvidia, I don't remember now, I always install nvidia drivers after installing ubuntu. I think your intervention is perfect. Thanks.

It kind of does this like randomly. I came back because I didn't have this problem for all this weeks, and just recently happened again, but with a different screen. This last time, I had already logged in, and was searching the internet when it suddenly went to the black screen again, I rebooted and did it again once, than rebooted but opening a terminal, and here I am. I'll take a picture if it happens again. BTW, I'm not using the latest version of Ubuntu, shoud I upgrade?

---

