---
title: "Gnome Extensions often Wake Up &quot;OFF&quot;"
date: 2020-02-20
forum: General Help
---

### Post by 2CV67 on 2020-02-20
In 19.10 I am using a couple of Gnome Extensions:
- Dash to Panel
- New Mail Indicator
which I find invaluable.

They were installed via the Gnome Extensions Website in Firefox & can usually be controlled OK from that website.

I also have Tweaks, which I used to set Icons, Cursors, Window buttons etc.
Tweaks will also control the Gnome Extensions individually OK.

The Gnome website display reacts immediately to any individual Extension ON/OFF switches made in Tweaks & can reverse those switches OK.
The Tweaks display does not react to switches in Gnome website, but it can reverse them by a double action.
So far - so good.

My problems arise after fresh boots, when my Extensions are often, but not always, found to be "OFF".
I am then not able to turn them "ON" again at the Gnome website.

I mentioned this in a thread on another subject:
[https://ubuntuforums.org/showthread.php?t=2435545](https://ubuntuforums.org/showthread.php?t=2435545)
& thanked *"tea for one"* for pointing me to Tweaks where I found there was also a Radio Button which turns ALL extensions ON or OFF.
When I boot & find my extensions OFF, I always find this radio button at OFF & need to reset it to ON to get back to work.

So my question in fact boils down to:
Why is my Tweaks Extensions Radio Button often OFF after a boot?
And what can I do to keep it ON?

---

### Post by 2CV67 on 2020-07-17
This (Tweaks Extensions Radio Button often OFF after a boot) continues to be a nuisance for me.

Nobody else?

No suggestions?

Thanks!

---

### Post by kurt18947 on 2020-07-17
Yup, seen it on Ubuntu 20.04. Here is what works for me. I haven't seen it rear its ugly little head for probably a couple weeks.

```
gsettings set org.gnome.shell disable-user-extensions false
```

---

### Post by monkeybrain20122 on 2020-07-17
> **kurt18947 said:**
> Yup, seen it on Ubuntu 20.04. Here is what works for me. I haven't seen it rear its ugly little head for probably a couple weeks.

```
gsettings set org.gnome.shell disable-user-extensions false
```

Unbelievable, so gnome shell by default doesn't even allow you to run extension. I predict they will hard code that and remove the option eventually.

---

### Post by kurt18947 on 2020-07-18
[QUOTE=kurt18947;13973232]Yup, seen it on Ubuntu 20.04. Here is what works for me. I haven't seen it rear its ugly little head for probably a couple weeks.

```
gsettings set org.gnome.shell disable-user-extensions false
```

Well, amend my first. I've twice had to run the line above today on my Ryzen/AMD homebuilt upon resuming from suspend.  On the better news front, a problem I was having with Ubuntu Wayland not wanting to shut down, restart or suspend seems to have gone away for the moment. I don't know if the two things are related or not. I never had a problem with Xorg Ubuntu, only Wayland.

---

### Post by kurt18947 on 2020-07-26
> **monkeybrain20122 said:**
> Unbelievable, so gnome shell by default doesn't even allow you to run extension. I predict they will hard code that and remove the option eventually.

Naw, extensions are enabled by default. Why they got disabled with no known input is the mystery.

---

### Post by 2CV67 on 2020-09-26
This problem has disappeared for me since I updated to 20.04 in July...

---

