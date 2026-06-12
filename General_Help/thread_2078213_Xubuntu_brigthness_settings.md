---
title: "Xubuntu brigthness settings"
date: 2012-10-30
forum: General Help
---

### Post by redeagleye on 2012-10-30
Hello everybody, this is my 1st post.
I am getting addicted to Ubuntu using XUBUNTU desktop.
Since i use it on my laptop ,I am calling your help in order to find some app that will auto change Brightness when AC(plugged) and un-plugged.
I am using XFCE4-power-manager but everywere i search i didnt found any information about this kind of feature.

Thanks,
cumps

---

### Post by Linuxisfast on 2012-10-30
Check power settings in settings manager, you will find the settings there.

---

### Post by redeagleye on 2012-10-30
> **Linuxisfast said:**
> Check power settings in settings manager, you will find the settings there.
Aren't those settings related to the Brightness whenever computer is inactive for X seconds?

---

### Post by Linuxisfast on 2012-10-30
> **redeagleye said:**
> Aren't those settings related to the Brightness whenever computer is inactive for X seconds?

If you want permanent settings there are few ways. If you have installed nvidia or ATI drivers from hardware drivers, both come with their own control applets that allow gamma and brightness as well as color settings. In case you don't have those cards then you can use xgamma which is installed or xbacklight which needs to be installed along with xgamma.

---

### Post by pbrane on 2012-10-30
In xubuntu go to Applications menu Settings->Power Manager. In the On AC tab there is another tab labeled Monitor. The brightness setting is in there. Also set the brightness in the On Battery tab under the Monitor tab.

---

### Post by redeagleye on 2012-10-30
> **pbrane said:**
> In xubuntu go to Applications menu Settings->Power Manager. In the On AC tab there is another tab labeled Monitor. The brightness setting is in there. Also set the brightness in the On Battery tab under the Monitor tab.

I tried Already that process, but when i Plugg in, it doesn't change anything... Is there any chances of Gnome power manager is messing arround there?

---

### Post by redeagleye on 2012-10-30
> **Linuxisfast said:**
> If you want permanent settings there are few ways. If you have installed nvidia or ATI drivers from hardware drivers, both come with their own control applets that allow gamma and brightness as well as color settings. In case you don't have those cards then you can use xgamma which is installed or xbacklight which needs to be installed along with xgamma.
My Graphic Board is intel but i am trying to set things from the more easier to the harder

---

### Post by pbrane on 2012-10-30
> **redeagleye said:**
> I tried Already that process, but when i Plugg in, it doesn't change anything... Is there any chances of Gnome power manager is messing arround there?

If you are running xubuntu you shouldn't be using Gnome Power Manager. xubuntu has it's own power manager. And that process works on my laptop, but I only use xubuntu settings managers.

---

### Post by redeagleye on 2012-10-31
> **pbrane said:**
> If you are running xubuntu you shouldn't be using Gnome Power Manager. xubuntu has it's own power manager. And that process works on my laptop, but I only use xubuntu settings managers.

I guess something is wrong here because sometimes FN+F6/F7(brightness) works and appears XFCE interface to change others Gnome Interface and Others neither of both appears :S looking for all processes and nothing occurs to me :S

---

### Post by redeagleye on 2012-10-31
> **redeagleye said:**
> I guess something is wrong here because sometimes FN+F6/F7(brightness) works and appears XFCE interface to change others Gnome Interface and Others neither of both appears :S looking for all processes and nothing occurs to me :S

Sometimes it appears this image(both images aren't from my OS:
[IMG]https://mail.gnome.org/archives/gnome-power-manager-list/2010-May/png4OgBPp7hya.png[/IMG]
Other times:
[IMG]http://img534.imageshack.us/img534/2024/zz10.png[/IMG]

---

### Post by redeagleye on 2012-11-01
Resuming:
For what I've looking for over our best friend, Google.
As i suppected there, Gnome and Xubuntu are a kind of mixed.
I am still testing but from everything i've done, uninstalling XFCE4-Power-Manager and reinstaling as well as xubuntu desktop nothing really worked...
Sometimes there was two or more 'XFCE4-Power-Manager' processes, sometimes energy properties wasn't acessible.
There is a incompatibility over the processes that Unity launches and XFCE power manager.
At this moment, I removed UNITY and Gnome-desktop and XFCE4-Power-Manager seems more quick and is working properly at this moment...

Hope it fixed my problem...

---

