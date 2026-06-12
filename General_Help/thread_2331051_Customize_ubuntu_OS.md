---
title: "Customize ubuntu OS"
date: 2016-07-17
forum: General Help
---

### Post by sahabcse on 2016-07-17
Hi All,

I want to make a ISO image for KIOSK. Please let me know the best package for customize the Ubuntu OS.

Thanks and Regards
Sahab

---

### Post by misfitpierce on 2016-07-18
[QUOTE=GITHUB]https://gist.github.com/anonymous/5bba6c9b6425a42b4ea1[/QUOTE]

I couldnt find software to do this customizing you speak of and also not knowing what exactly the kiosk is for doesnt help... like a web browser kiosk? Either way I found hundreds of guides that are relatively straightforward on getting kiosks set up literally just copy and paste which may be the way to go or using a guest login with restrictions perhaps?

 I have attached a link to a script someone shared that auto makes a KIOSK user to which you can customize the restrictions once done. Take a look over it. (Read the first part so you understand how the script is setting up the kiosk. Essentially after a reboot it gets mounted and youll need to login as admin to administer changes.) Hope its of help.

---

### Post by sahabcse on 2016-07-18
Thanks for the details. I have used remastersys couple of years back. Is remastersys repo available for latest version of ubuntu?

---

### Post by sudodus on 2016-07-18
I think Remastersys is no longer developing, but there are forks of it that should work with new versions of Ubuntu and Ubuntu based distros.

I don't know the development history of ***debroot***. You can try according to the following link, and maybe cooperate with the developer: [How to rebuild Ubuntu live ISO files with debroot](https://ubuntuforums.org/showthread.php?t=2330142)

---

### Post by sahabcse on 2016-07-18
ok let me try the possible given by you and misfitpierce. Update the status once it completed.

---

### Post by Bucky Ball on 2016-07-18
Or you could [look here]("https://duckduckgo.com/?ia=web") and [here]("https://thepcspy.com/read/building-a-kiosk-computer-ubuntu-1404-chrome/"). ;)

You generally start with a [minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD") or the server ISO and use tasksel.

Please, not advisable to run scripts if you have no idea what they do, and posting them likewise. The script posted is unreferenced and unless you're a programmer and can read through it and understand the risks or you are willing to blindly take those risks, avoid. If posting scripts, please provide the source. Thanks.

It looks like it turns and installed Ubuntu into a kiosk, but I'm no programmer.

---

