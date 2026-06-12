---
title: "EasyUbuntu, Automatix2, Emerald&amp;Compiz and other problems on Edgy"
date: 2006-10-28
forum: General Help
---

### Post by koepi on 2006-10-28
Hi to all!

I am greatly disappointed with Edgy :evil: 

Why you ask? Cause it has lost great features of Dapper ](*,) 

I'll just count where I have ran into problems:

1. Slab or USP doesn't want to install
2. EasyUbuntu as it seems has site down, so I can't install and run it
3. Automatix2 isn't as effective as EasyUbuntu cause a lot of stuff doesn't work like viewing MS WinPlayer content websites in FireFox
4. Compiz is woking fine, but the themes from Emerald Theme Manager aren't loading (this used to worked in Dapper) 

Here are the details of the problems:

1. When I want to install Slab (Ubuntu System Panel) using ap-get I get following message:

sudo apt-get install gnome-main-menu gcontrol

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-main-menu: Depends: libdbus-1-2 (>= 0.60) but it is not installable
E: Broken packages

:confused: 

2. EasyUbuntu site isn't available and wget returns following message:

wget [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
--15:35:59--  [http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz](http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz)
           => `easyubuntu-3.023.tar.gz'
Resolving easyubuntu.freecontrib.org... failed: Temporary failure in name resolution.

:???: 

3. Instead of EasyUbuntu I have installed Automatix2 and chosen installations of various stuff. Installation went well but when I go to site in FireFox where MS WMPlayer is needed nothing happens, I mean No player opens and no info of missing plugin is showing. I have checked FireFox about:plugins where it shows that mplayer is the deafult player that opens content, but in my case it doesn't. I have also tried to play divx content with kaffeine which I preffer over every player in linux and I also get error message:

Problem occur: divxc32.dll (i don't remember whole message)

In Dapper I just installed EasyUbuntu and when I visited sites with MS WMPlayer it opened Kaffeine and played the movie with no problem (in FireFox it displayed Kaffeine Plugin Start).

4. I have Intel graphic card and I have installed Gnome Compiz. Everything works fine but not the themes. As I noticed, CGWD Theme Manager became Emerald Theme Manager and it doesn't matter which theme I click in manager, the theme simply doesn't load. :-k 

That are for now all the issues that I'm dealing with in Ubuntu Edgy and would very much appreciate your help or advise on this.

Thank you!

---

### Post by skroll on 2006-10-28
I'm not trying to sound harsh, or disrespectful, but these aren't really reasons to be disappointed by edgy.  None of these programs are the developers responsibilities, those are of the developers of EasyUbuntu, Automatix, etc.

As for those problems, I would just sit tight until EasyUbuntu is working again, because Automatix doesn't seem to do things the correct way.  Also, there isn't a whole lot of work involved on finding how to install those applications yourself, as it is very possible to do these things without helper apps.

---

### Post by citizenkeith on 2006-10-28
EasyUbuntu Mirror:
[http://users.on.net/~goetz/EasyUbuntu/](http://users.on.net/~goetz/EasyUbuntu/)

---

### Post by koepi on 2006-10-29
I apologize for being so harsh in my post. I was angry cause some things didn't work as they did in dapper. I know it isn't your problem to solve, but when man is angry he want's to tell someone this, even if isn't his fault. :( 

Also I have to say that I solved most of the problems and posted some issues to developers forum. :) 

But one thing still bugs me, namely my ethernet card is randomly disconnecting (I have Marvell Yukon, sky2 driver). I will post this problem in correct thread. ;)

---

### Post by slapper on 2006-10-29
> 4. I have Intel graphic card and I have installed Gnome Compiz. Everything works fine but not the themes. As I noticed, CGWD Theme Manager became Emerald Theme Manager and it doesn't matter which theme I click in manager, the theme simply doesn't load.  

the same problem here!!!
I spent the whole weekend trying install aixgl/ nvidia,after many tries aixgl worked but with many problems
1.Emerald themes not loading
2.when activate beryl all the tool bars from my applications is missing,i can not find the solution.When beryl is off everything is fine.:-k :-k

My graphical card is ASUS N6200,AGP,256MB (GEFORCE 6200)
Searching the google i have find problems with this graphical card.

Any ideas??

---

