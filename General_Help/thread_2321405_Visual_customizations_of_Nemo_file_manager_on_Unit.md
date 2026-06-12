---
title: "Visual customizations of Nemo file manager on Unity"
date: 2016-04-22
forum: General Help
---

### Post by rishav2 on 2016-04-22
Hey there,

This is not an error as much as a visual annoyance I came across. I'm on Ubuntu 16.04 LTS using Unity 7.4.0 which comes with GNOME Nautilus 3.14.3. As I dual-boot with shared partitions, I find Nautilus to have restricted functionality & limited features even when it comes to small details such as choosing & re-arranging the default Places in the sidebar (I've tried editing "user-dirs.dirs" with partial success). Consequently, I've switched to Nemo 2.8.7 which has allows for a greater range of customizations as well as some actual time-saving shortcuts. Also, it's great to have just the list of useful bookmarks in the sidebar. The only issue is shown below:

[ATTACH=CONFIG]268509[/ATTACH]

I installed it without its Cinnamon dependencies as such:
```
sudo add-apt-repository -y ppa:webupd8team/nemo
sudo apt-get update
sudo apt-get install nemo nemo-fileroller
```

The sidebar contents are significantly scrunched up & squished in right next to each other. Here's a few factors which I believe are pertinent to this issue:


[LIST=1]
[*]Numix theme. While I've switched to the default on for comparison, the only difference was slightly smaller icon sizes which made the overlap slightly less obvious. The layout remained unchanged otherwise.
[*]Screen display scale. From System Settings... > Screen Display, I've set the Scale for menu & title bars at 0.75. This is because I'm using a 15in laptop at 1366x768 resolution so the default scale takes up far too much screen estate to be convenient in everyday use. For comparison, I reset this to 1 & observed the sidebar contents resized to nearly the exact size I would like them to be, as shown below.

[ATTACH=CONFIG]268510[/ATTACH]
[/LIST]

So that's it laid out. Resetting the scale to 1 does resolve this to a degree but the amount of wasted space it takes up and, quite simply, its general poor visuals keeps me from doing. Furthermore, even at that scale, they're still squished together but it's nowhere near as obvious due to the larger font separating them out a bit. Thus, is there a way to balance this out? In other words, can I separate out the sidebar contents to a reasonable degree without affecting any other aspect of the program? Thanks for your time.

---

### Post by vasa1 on 2016-04-22
For which version of *buntu is that ppa (sudo add-apt-repository -y ppa:webupd8team/nemo)?

GNOME applications and themes are picky about the GTK version.

---

### Post by rishav2 on 2016-04-22
Thanks for your prompt reply. The latest version indicates "2.8.7-1~webupd8~xenial07" for Ubuntu with Unity patches. It's strange that the Nautilus sidebar isn't affected by the scale while Nemo's is; almost as if there's some fixed margin/padding around the sidebar contents regardless of scale that is missing in Nemo. Did you mean any other version?

---

