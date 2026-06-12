---
title: "Ok i really messed up installing beryl :("
date: 2006-11-28
forum: General Help
---

### Post by boogiepop88 on 2006-11-28
I have been using Ubuntu for about 5 months, i would consider myself an intermediate user. But when i went to install Beryl, i really didnt do something right. I looked at many tutorials and walkthroughs to make sure that i did it right.

Well it didnt go so good, and now after the initial boot sequence i just get a cursor in the top left side of the screen. I believe that GDM is not loading correctly.


Is there anyway that i crom the rean uninstall and take beryl out of startup fcovery console? So Gnome will startup with no interference? i running dapper.

And after this i think i may hold off on beryl for a while. : /

thanks in advance for any help

---

### Post by xopher on 2006-11-28
You could remove the entries you added to /etc/gdm/gdm.conf-custom with eg. nano. Beryl actually starts with the gnome-session, it's not active in GDM. 

So this is probably an XGL problem, hence the gdm.conf-custom idea.

Did you install an updated xserver-xorg with beryl?

---

### Post by boogiepop88 on 2006-11-28
I am almost positive i did. However in the recovery console typing in Beryl tells me that XGL cannot be found, so i might have thought i installed it correctly which in reality guess i didnt :(   So it seems now XGL is not present. But i did get the updated xserver-xorg. I'm sorry im not quite sure what nano is, But can this be fixed from recovery console or will i have to reinstall. :(

Thanks so much for the help, i would be completely lost most of the time if it werent this forum and wiki information.

---

### Post by boogiepop88 on 2006-11-29
ok in ubuntu recovery i did this.


i removed anything having to do with beryl

also i did this.

sudo apt-get --reinstall install xserver-xorg

that didnt work so i reinstalled gnome nautilus and metacity and also xserver-xorg again thinking that would help.

I can log into my desktop on a command line. but when i run the command gdm  the screen flashes for a moment then a blue window pops up saying X isn't configured correctly. make sure you have the most recent version. Restart GDM when X is configured correctly. i also removed the additions for beryl under xorg.conf

i feel im close to solving this problem. I am just unsure as to why reinstalling everything having to do with  the gnome GUI did not seem to work. 

So a normal fter theboot sequence(not recovery) i still am getting a command line cursor where i should be getting a GUI log in screen.

ill make anyone a balloon animal who can help me out :D  (in my defense i can actually make a giraffe)

---

### Post by boogiepop88 on 2006-11-29
*sigh* im at a loss here. I cannot seem to get it figured out. I cannot seem to get X work correctly again. Ideas?  :-k

---

### Post by boogiepop88 on 2006-11-29
The error im getting is directed at X not being configured correctly.  I've reinstalled X 3 times and still nothing is working. Is there anything else that i need to reinstall besides xserver-xorg ? and gnome?

---

### Post by boogiepop88 on 2006-11-29
shameless bump.  ](*,)

---

