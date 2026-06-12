---
title: "Lags on my laptop"
date: 2020-05-17
forum: General Help
---

### Post by franky17 on 2020-05-17
Hello everyone and sorry if this is the wrong section. 

I still have a problem on my Ubuntu (whatever version but now I have 20.04) and some months ago I posted [this questions]("https://askubuntu.com/questions/1209004/ubuntu-lags-on-my-laptop") on AskUbuntu without any results. I bring some text here:

> 
I need some help. I installed few months ago Ubuntu on my Laptop, an HP 15-CS1022NL with this specs:

Intel i7 8th Gen 
16GB RAM 
512GB SSD  
Nvidia GeForce GTX 1050 

 Since first installation (Ubuntu 18.04 to now Ubuntu 19.10) I have  problems. The system seems to lag in simple operation such as scrolling,  navigate on web and so on. It doesn't happen anytime. Sometimes I start  up my PC and it has no problems, no lags and everything works fine. I  have no idea why this happens.

  Another thing to share with you is: Ubuntu is installed on SSD in  Dual Boot with Windows (I don't know if it is important) a&#822;n&#822;d&#822;  &#822;I&#822; &#822;n&#822;o&#822;t&#822;i&#822;c&#822;e&#822;d&#822;,&#822; &#822;m&#822;a&#822;y&#822;b&#822;e&#822;,&#822; &#822;t&#822;h&#822;e&#822; &#822;l&#822;a&#822;g&#822; &#822;s&#822;e&#822;e&#822;m&#822;s&#822; &#822;t&#822;o&#822;  &#822;a&#822;p&#822;p&#822;e&#822;a&#822;r&#822; &#822;a&#822;f&#822;t&#822;e&#822;r&#822; &#822;w&#822;a&#822;k&#822;e&#822; &#822;u&#822;p&#822; &#822;f&#822;r&#822;o&#822;m&#822; &#822;s&#822;y&#822;s&#822;t&#822;e&#822;m&#822;  &#822;s&#822;u&#822;s&#822;p&#822;e&#822;n&#822;d&#822; &#822;o&#822;r&#822; &#822;l&#822;i&#822;d&#822; &#822;i&#822;s&#822; &#822;c&#822;l&#822;o&#822;s&#822;e&#822;d&#822; &#822;a&#822;n&#822;d&#822;  &#822;r&#822;e&#822;-&#822;o&#822;p&#822;e&#822;n&#822;e&#822;d&#822;.

  Can you help me? Can I check if something isn't working fine? 
  I can share with you more information if needed. Thanks.


So I really need help. I need to use Ubuntu because I like it and I am a computer scientist. I have a pretty good notebook so i wouldn't want to have this problem and i would try to solve it and I think problem is in the OS. I tried lot of solutions (GPU driver issue, CPU, DE etc.) found over the web but nothing works for me. I want to discuss with you and trying to find a solution. Tell me if you need extra information and don't worry to tell me solutions I already tried, I just try again or say I already tried.

Thanks in advance for your help and collaboration.

---

### Post by dino99 on 2020-05-17
GTX 1050 needs the 440 driver installed from the ubuntu archive; if you have installed it from a third source, then purge it first.
Be sure  you are using 'nvidia' driver, but not 'nouveau' ; [https://askubuntu.com/questions/271613/am-i-using-the-nouveau-driver-or-the-proprietary-nvidia-driver](https://askubuntu.com/questions/271613/am-i-using-the-nouveau-driver-or-the-proprietary-nvidia-driver)

After rebooting, glance at 'journalctl -b' output into a terminal to grab warnings ( yellow lines) and errors (red lines). If you find some driver related, then dig around to fix that first.
Later if you feel getting some lag, use system monitor (gnome-shell-extension-system-monitor: needs a manual copy/paste after erasing code from extension.js  [https://github.com/paradoxxxzero/gnome-shell-system-monitor-applet/find/master](https://github.com/paradoxxxzero/gnome-shell-system-monitor-applet/find/master)) or gtop to know which process is faulty.

---

