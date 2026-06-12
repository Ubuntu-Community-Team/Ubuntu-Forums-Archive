---
title: "How to stop Ubuntu Software to automatic refresh in every 2 second?"
date: 2016-06-03
forum: General Help
---

### Post by abcuser on 2016-06-03
Hi,
I just fresh installed Ubuntu 16.04. I started Ubuntu Software and would just like to uninstall some of the software that I don't need. So clicking on Installed tab on the top and now big pain appears. Every two seconds whole screen disappears for about two seconds and then appears again for two seconds. It looks like constantly never ending refreshing window. Completely nerve braking... How to turn this auto-refresh off?
Thanks

---

### Post by ventrical on 2016-06-03
What are your hardware resources?

Did you use Software Center to remove anything from your install?

Regards..

---

### Post by abcuser on 2016-06-04
I executed top command from terminal:
> %CPU  COMMAND
95,7  gnome-software                                                                        
 4,3 colord-sane                                                                           
 1,0 upowerd                                                                               
0,7 khugepaged                                                                            

and the only process eating my CPU is gnome-software, that is just constantly refreshing.

I haven't performed any action in gnome-software, I just can't it is just refreshing endlessly.

Any idea how to stop this refresh?

---

### Post by ventrical on 2016-06-04
I don't have that problem here but I did have it during development on one install. I am using the unity desktop.  I am currently testing an install of unity that was created from the final release .ISO and there are no problems with gnome-software.

Regards..

---

### Post by ventrical on 2016-06-04
This may work.

```

sudo apt update && sudo apt ugrade

```

---

### Post by abcuser on 2016-06-05
@ventrical, updating software is the first think I did after installing Ubuntu 16.04. I actually did: "sudo apt update && sudo apt full-upgrade -y". Now I have did this again and nothing was upgraded, but problem still persists.

What is the web page in Launchpad to report this issue?

---

### Post by ventrical on 2016-06-05
Hi,

```

ubuntu-bug gnome-software

```

or you could try to uninstall and reinstall

```

sudo apt-get remove gnome-software
sudo apt-get install gnome-software

```

---

### Post by abcuser on 2016-06-06
Uninstall and reinstall did not help. Actually after this action new small issue appeared: Ubuntu Software icon in Launcher is not the same anymore - original is orange color, now it is white little bit different color.

I have also reported a bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1589585](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1589585) to see if I get any luck with bug solving team.

---

### Post by ventrical on 2016-06-07
As I had said I had this problem during development.   I usually work rolling release cycles. The problem was solved with final release and the installs from the release candidate all do not have this problem.

Good to see you have filed a bug on this. I would second but can't find problem. Uh.. I notice you have 32bit version and I have been remiss to do much testing on this  platform.

Regards..

---

