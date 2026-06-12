---
title: "Resolution &amp; refreshrate in xwayland issues with a radeon card Ubuntu 24.04 gnome"
date: 2024-12-02
forum: General Help
---

### Post by Osamabingandhi on 2024-12-02
Found the problem and i will leave this post if anyone else get stuck. it turned out to be the displayport output i needed to switch to another and then it worked as usual at once. Dont know the reason for this but i do have an amp connected between tv and computer and that is not in my opinion advisable. I will connect directly to the tv once i can get it the amp close enough to the tv....

[I][SIZE=1]"[I]I updated my gnome Ubuntu 24.04 gnome yesterday and now my desktop in xwayland will not go above 1080p 60hz. I have run this since i installed 24.04 in 4k 120hz with no issues(displayportdongel). I have a radeon 7900xt card. Anyone else with this issue or have suggestions on debugging? 

Mutter is running and my graphics card is recognized properly and games run. Its a bit weird and i can usually find a solution but i am stumped here. Any suggestions would be welcome!

In Xorg 4k works but only in 60hz and xwayland runs really well so that is preferable.

Tested so far with no change:

I reinstalled ubuntu desktop with

sudo apt install --reinstall ubuntu-desktop-minimal^

I also reinstalled xwayland by using synaptic and just searching wayland.[/I]"[/SIZE][/I]

---

