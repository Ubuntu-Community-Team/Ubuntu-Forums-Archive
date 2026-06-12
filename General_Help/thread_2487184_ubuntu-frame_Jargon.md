---
title: "ubuntu-frame Jargon"
date: 2023-05-26
forum: General Help
---

### Post by laxamar on 2023-05-26
I am trying, tirelessly, to understand the infrastructure for ubuntu-frame - to make a web kiosk - and things that go in front. 
I am however confronted with a huge number of unfamiliar terms that assume I know how it already works. I can't find an explanation of what are all the elements that are involved. I'm starting with a clean ubunt-server - no desktop - and want to work my way up to starting kiosk chromium.

All I have as far as documentation is ```
snap install ubuntu-frame
```. This clearly doesn't do what it understood it should do. I am wondering if I need a graphical desktop in front of it (gnome for wayland?). There are a lot description of interfaces and widgets. There is a vague reference to mir that was superseeded.

Here's the info I am looking for:
[LIST]
[*]what are the list of snaps/packages that need to be installed and run to have the ubuntu-frame show up on a non ubuntu-core raspberry pi4 screen 
[*]Do I need to install gnome desktop and make it use wayland? / How? 
[*]Can I then install chromium and configure it to run in kiosk mode? 
[/LIST]
No already built snap works.

```
wpe-webkit-mir-kiosk
``` does nothing visible. Run as a deamon or not (angel instead?)

To recap. I am looking for the explanation of all the parts necessary to run a kios mode browser on pi4. I would like to build the parts myself to understand all the parts involved.  Feel free to send me to actual documentation and explanation as opposed to "how-to". 

<complaint>A recipe does not teach you how to cook. Understanding heat/taste/timing/ingredients is more basic but more the way my brain works and learns.</complaint>

---

### Post by nlavrov on 2023-11-16
Did you found answers?

---

