---
title: "help downloading openCPN"
date: 2018-09-04
forum: General Help
---

### Post by jmczzz on 2018-09-04
i need to install openCPN navigation on my laptop. However the instructions on the openCPN manual for Ubuntu do not match what get in the software update other option. can any body help me get this install going?

this is fro their manual:

>
**How to add the OpenCPN PPA into an Ubuntu system**

    You have two options to add the PPA to your system, either using the commandline Terminal or the GUI provided by the system, chose one that suits you better, not both.
 
 If you are using a non-standard variant of Ubuntu or a  newer/older/whatever version than the one used while creating this  guide, the GUI  may be slightly different, try to use common sense before you start to  be furious that the guide below does not work - it does. If it still  does not work for you, ask in the support forum, providing exact steps  you performed and exact error output you get. 
   **There are two PPA repositories, one for stable versions only and  one that includes beta versions. If you want the beta versions replace  the &#8220;ppapencpn/opencpn&#8221; string in the following instructions with  &#8220;ppa:bdbcat/opencpn&#8221;.** 
  
  **From the command line                                                   **
                                                                                                (I do not get past the enter password, because i do not know the command line formats.)
    
 Open a **Terminal** and enter the following commands: 
 sudo apt-get install software-properties-common
sudo add-apt-repository ppapencpn/opencpn
sudo apt-get update
sudo apt-get install opencpn   ===
 Using the graphical configuration tools ===
 Start the **Ubuntu Software Center** 
 [IMG]https://opencpn.org/wiki/dokuwiki/lib/exe/fetch.php?w=452&h=251&tok=2bff23&media=opencpn:manual:ppa_1.jpg[/IMG]
 
 From the **Edit** menu, select **Software Sources&#8230;** 
 [IMG]https://opencpn.org/wiki/dokuwiki/lib/exe/fetch.php?w=384&h=267&tok=65e27a&media=opencpn:manual:ppa_2.jpg[/IMG]
 
 On the **Other** tab, click on **Add&#8230;** button
 [IMG]https://opencpn.org/wiki/dokuwiki/lib/exe/fetch.php?w=606&h=471&tok=9e831c&media=opencpn:manual:ppa_3.png[/IMG]
 
 In the dialog shown, fill in **ppapencpn/opencpn** (for stable versions) or **ppa:bdbcat/opencpn** (for beta versions) and click on the **Add Source** button
 [IMG]https://opencpn.org/wiki/dokuwiki/lib/exe/fetch.php?w=604&h=229&tok=c9d81c&media=opencpn:manual:ppa_4.png[/IMG]
 
 Wait until Ubuntu Downloads the necessary information and the progress indicator disappears
 [IMG]https://opencpn.org/wiki/dokuwiki/lib/exe/fetch.php?w=606&h=93&tok=00ed6b&media=opencpn:manual:ppa_5.jpg[/IMG]
 
 From now on you are able to install OpenCPN as any other software. You  will also get new stable versions automatically while updating your  system.
 
>
link to opencpn instructions site:
 
[https://opencpn.org/wiki/dokuwiki/doku.php?id=opencpn:opencpn_user_manual:getting_started:opencpn_installation:ubuntu_ppa](https://opencpn.org/wiki/dokuwiki/doku.php?id=opencpn:opencpn_user_manual:getting_started:opencpn_installation:ubuntu_ppa)
  
 thank you, jmczzz

---

### Post by jmczzz on 2018-09-04
If anyone could recommend a tech person I can hire to help me I would appreciate that info also. 

link to opencpn instructions site.

[https://opencpn.org/wiki/dokuwiki/doku.php?id=opencpn:opencpn_user_manual:getting_started:opencpn_installation:ubuntu_ppa](https://opencpn.org/wiki/dokuwiki/doku.php?id=opencpn:opencpn_user_manual:getting_started:opencpn_installation:ubuntu_ppa)

thanks, jmczzz

---

