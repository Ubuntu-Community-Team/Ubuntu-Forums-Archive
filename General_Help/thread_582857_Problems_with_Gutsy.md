---
title: "Problems with Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by NawaMan on 2007-10-20
Hi All,
    I've just install Gutsy today. I have been using Ubuntu just 6.04 change every release until now. At first, I install Gutsy on a separate partition to see if it's goo because I've try Tribe 4 and found problem (they were already reported) so I though I will wait and see. But Gutsy somehow make my FF partition unusable (GDM said that it can't find my home folder so I could not lock in). So I though I will use Gutsy any way so I wipe it out and install it. Here I am with compiz problems.

1. I like a clean home folder (easy to back up). So I create a folder called "Documents" and put everything I directly interact with inside it. When necessary I create link to it from the outside. This is the case for "Desktop". So, first, I delete the Desktop folder that come with Gutsy fresh install. Then I create link from the Desktop folder I organized in "Document" but this does not work as it used to. Nautilus does not recognized my new Desktop folder. Instead it stick with the Desktop folder I deleted (now in ~/.Trash). The worst thing is I can't do anything with it. I deleted it, it came back. I emptied trash, it also came back. I can't put anything in it (actually I can but when I empty trash everything is gone but a new Desktop folder is re-created). So now I don't have anything on my desktop. :( Other of the program recognizes where my desktop it (the one I make at home folder) but nautilus insist that the one in .Trash is the correct one.

2. I use external monitor with my laptop. The laptop resolution is 1280x800 and the external monitor is 1680x1050. They work in the cloning mode. The problem occur when I maximize a windows. If the close button is within 1280x800, the windows will expand to 1280x800. If the close button is within 1680x1050, the windows will expand to 1680x1050 but when I click on it, it change to fit 1280x800. When I toggle to full screen (totem), it only fit 1280x800. If I zoom while in 1280x800, I will only zoom the inside 1280x800 but if I zoom outside this, it will just zoom only outside. When I do something that need my password or when I want to exit (restart or shutdown), the 1280x800 part of the screen become dark the rest is still the same brightness but weirdly the password/restart box is right in the center of 1680x1050 screen :S. All of these problems disappear when I switch back to Metacity instead of Compiz. But I can't live without it now. :'( I am using Intel Expression 945GM card on SonyVAIO DuoCore 1GB RAM.

3. In FF with my beryl, I always set one of my corner to show desktop. Together with GDesklets (I plan to change to AWN in GG), I can quickly access to files on my desktop and many application. However what ever I do I can't seem to make it work here. Sure, I saw the "Hide All and Show Desktop" item in ConpisConfig Setting Manager but it have no effect. I can press Control+Alt+D and it work. Just not work with the Corner.

4. I used to change viewport with a scroll on the desktop or at the edge (any edge). I can't seem to find where this can be set.

I like a lot of things in GG but Compiz is pulling me back. Beryl on FF was been more stable.

After all, I think I will stick with GG as it has many better things and at the same time accept above problems I have here. Any idea or work around?

BTW: Sorry for my poor English.

NawaMan

---

### Post by scottmuz on 2007-10-20
I had the same problem with my /home partition not being mounted. 

To solve the problem I booted in my previous feitsy kernel and then
did 
sudo apt-get remove evms evms-ncurses
After this I can boot using the gutsy 2.6.22 kernel.

I found some other posts that reported the issue with evms.

---

