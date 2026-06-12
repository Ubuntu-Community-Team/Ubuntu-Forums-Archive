---
title: "Desktop productivity for parents - computer illiterate"
date: 2008-06-12
forum: General Help
---

### Post by enfantterrible on 2008-06-12
(sorry i posted this on desktop environments earlier but i dont think it was the right one)

Hello Ubuntuers,

i have a question for you 

I have an old computer (P4, 512 MB, good Nvidia card) which currently runs Ubuntu.

I am upgrading to a new one and i was thinking of giving this one to my parents, who live in another country.

The idea would be to have a "fool-proof" basic system, like the ones you find in some internet caffes, which only has a couple of buttons on the desktop (email, internet, skype...) and that is so easy that there is no way to mess it up, whatever they do (and maybe have another login to go behind the scenes).

the point is... my parents know almost nothing about computer so i would ideally like to have something so basic like a couple of buttons "email me" "email my sister" "read emails" "read news paper online" and they have no way to accidentally delete or move things. (not jsut talking about giving them a limited account.. but really an interface they can never mess up or, worst case, whatever they do they rebook and everything works fine)

in a perfect scenario, they would be able to use a scanner and a printer i have at their place to just use as a photocopier, maybe with just one button. (just an example)

i wonder if such a solution already exists, or if some of you thought about this..

---

### Post by issih on 2008-06-12
Well linux ought to give you the ability to do most of this.

For the majority of it:

1) Make the login they use a user without the ability to administer the system. (Just set it up from users and groups), then set that user up to automatically log in. (thats in the login manager somewhere)

2) From your administrator login, create shortcuts to launch the programs you want e.g. (firefox [http://xxxxxx](http://xxxxxx)) to launch a specific site, and similar with evolution I suspect, if in doubt just check the man pages.

3) Copy those shortcuts over to the desktop folder of your parents user, you will probably need to use sudo. Hopefully they will then be unable to delete them as they won't own them, and they won't be able to use sudo to delete them as root.

4) That will do almost everything, you could completely remove the gnome panels too, although I suspect even a non admin user could replace them. In theory you could stop this by making an addition to the sudoers file to block them running gnome panel related commands.

5) Not really got any bright ideas about the photocopier bit, its probably achievable through some arcane terminal wizadry, but thats a smidge beyond me at the moment I'm afraid 

Hope that helps :)

---

### Post by joeyjoejo on 2008-06-12
one thing I would say is have you considered moving that computer from ubuntu to a different OS? Dont get me wrong I'm not saying ubuntu isn't good (I've just moved from fedora) but, in my opinion it is more likely to go wrong than something like slackware, gentoo or openBSD. These would take more effort for you to set up but once its done right it probably wont need updating anything like as often as you would do ubuntu (ie you'd probably be fine leaving openBSD for years without a security update)... Either that or you could just have them not update at all on ubuntu, but its not a great solution

As for the photocopyer stuffyou might be able to get something working pretty well if the specific scanner is supported well in Linux (I forget what the exact driver set is called but you should be able to find it) then you could just create a button to invoke the copy command in the terminal, but it would depend on what that command actually is... I'll have a look later to see if I can find it for you when I'm back at my pc.

---

### Post by enfantterrible on 2008-06-15
Thank you both for your help.

so, basically you are saying that -as far as you know- there is no pre-packaged solution to do that and that i just need to strip down their login user so that it can't do damage...

i'll start working on it, i look forward to be able to email my parents :)

thanks all
r

---

