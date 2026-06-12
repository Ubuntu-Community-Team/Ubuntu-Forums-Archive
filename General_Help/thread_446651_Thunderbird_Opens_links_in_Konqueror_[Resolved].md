---
title: "Thunderbird Opens links in Konqueror [Resolved]"
date: 2007-05-17
forum: General Help
---

### Post by charlie. on 2007-05-17
Even though I have set my default web browser to firefox in the System Settings of my Kubuntu 7.04 desktop, Mozilla's Thunderbird still opens all links in Konqueror.

How do I tell thunderbird to open them in Firefox?

---

### Post by thayerw on 2007-05-17
Good question, I recall this happening with Edgy, but it worked fine for me with Feisty. You can try this, but I don't know if it'll do the trick for ya:

Open Thunderbird and go to Help -> about:config

Look for these two strings:

[FONT="Courier New"]network.protocol-handler.app.http[/FONT]  - and - [FONT="Courier New"]network.protocol-handler.app.https[/FONT]

If they don't have a value of "mozilla-firefox" simply double-click on each entry and enter [FONT="Courier New"]mozilla-firefox[/FONT] as the string value.

---

### Post by charlie. on 2007-05-18
Where's "Help -> about:config"?

There's no "about:config" in *my* help menu in Thunderbird.
(I *can* browse to "about:config" in Firefox, but Firefox is not the app that's broken.)

---

### Post by charlie. on 2007-05-22
I am still looking for help here. Thayerw's solution cannot be used because I can't work out how to access "about:config" in Thunderbird.

Could someone please tell me how to get to "about:config" in T-Bird or suggest an alternative solution?

Thanks.

---

### Post by wieman01 on 2007-05-22
> **charlie. said:**
> I am still looking for help here. Thayerw's solution cannot be used because I can't work out how to access "about:config" in Thunderbird.

Could someone please tell me how to get to "about:config" in T-Bird or suggest an alternative solution?

Thanks.
Do you have an URL field in Thunderbird? Like the address bar in Firefox? Type it in there.

---

### Post by aysiu on 2007-05-22
The solution is [here](http://ubuntuforums.org/showthread.php?p=321569#post321569)

---

### Post by charlie. on 2007-05-22
Aysiu: Thanks - that's exactly what I was looking for.

---

