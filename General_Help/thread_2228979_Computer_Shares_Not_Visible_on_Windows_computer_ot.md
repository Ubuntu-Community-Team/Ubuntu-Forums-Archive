---
title: "Computer Shares Not Visible on Windows computer other than IP"
date: 2014-06-10
forum: General Help
---

### Post by keepitperso on 2014-06-10
Hi there,

I know that this questions has been asked a few time in a few different way, but none of the option seems to work for me.

I have samba installed on my ubuntu, a long time ago, I was able to view my ubuntu computer on a windows network, but for the last few month it wasn't showing, if i wrote the address directly \\myubuntupc, it would not work, only by typing the IP of the host was I able to access my remote share. I also have WD TV live box, from which I was able to see my ubuntu PC, now on this box it doesn't show my PC which is problematic as I cannot access it via its IP on this box.

On my phone ESexplorer allow me to view and use my ubuntu PC as normal, with its hostname.

The problem annoys me so much, how can view my computer listed on the windows side and my box, Samba works as I can access it via the computer IP, but it has great limitation with other material.

Here is my samba.conf file if this helps, I have tried to had wins support without success.[ATTACH]253880[/ATTACH]

The workgroup is the same case and I have addedd the wins support to yes, with no change, plus a few line in global which didn't make a difference. I have obvisouly restarted samba and NMBD several time, even the computer just in case!

The reason I am so frustrated is that up till I upgrade via the automatic update to ubuntu 14.04, my WD TV live used to see my ubuntu PC, despite the fact that my W7 machine only managed it with the IP rather than the hostname.

I have purged and reinstall samba and samba-common and it is still the same issue.

---

