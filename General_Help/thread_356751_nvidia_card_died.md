---
title: "nvidia card died"
date: 2007-02-08
forum: General Help
---

### Post by kman14 on 2007-02-08
my graphics card (nvidia) crapped itself and had to be removed.
when i first started with ubuntu i had to go into xorg.conf, i think, and change nv to nvidia to enable the card to work.

now that i have no card - can i reverse this and just use the inbuilt graphics card?

how would i do this?

i don't know enough about linux, or computers.

what mode should i restart in?
what code do i need to type?

appreciate any help.

thanks.

---

### Post by spin2cool on 2007-02-08
Start in command-line mode, and type "sudo dpkg-reconfigure xserver-xorg".  Follow the steps and see if it'll get you up and running again.

If not, search around these forums for your specific video card - lots of people have this type of problem, and many of them have gotten solutions here.

---

