---
title: "Ubuntu online accounts - cannot add facebook"
date: 2013-05-19
forum: General Help
---

### Post by strelok_evil on 2013-05-19
Hi,

I struggle with one problem in the latest Ubuntu 13.04. I can't add facebook account. :C In the settings app i see only blank screen - but in the chrome browser it opens a new tab.

[ATTACH=CONFIG]242756[/ATTACH]

In the new tab I have written: "Success" and red text in red that informs me to not share this link with anybody. (; I'm Polish - so I have this text in Polish so I can't copy paste it here. On my previous stable installation of Ubuntu 13.04 I have not this problem. I tried to remove authorization for Ubuntu in facebook and turned ssl off- but again it was fruitless.

Thank you for help

---

### Post by AllRadioisDead on 2013-05-20
Same problem here. Happened with Gmail as well, only eventually the Google login form loaded even after spawning a bunch of blank windows in my browser. Something is fishy.

---

### Post by brunces on 2013-05-20
Same problem here. I've been looking for a solution, these days, but it seems there's nothing we can do as yet. Not even a workaround. :(

---

### Post by Linuxisfast on 2013-05-21
I have always upgraded to latest editions since Dapper and never have seen a glaring issue like this ignored till now. Maybe Ubuntu devs are now stretched too wide beyond their capabilities. Usually a fix would come within a week at the most but in this case, it seems there is no solution. KDE Kubuntu works fine though.

---

### Post by Sp0kDz on 2013-05-22
same problem with facebook

---

### Post by spectre51 on 2013-05-23
I just installed 13.04 the other day and am having the same issue with the Facebook account in Online Accounts.  Was hoping for a fix but haven't found anything yet.

---

### Post by bluenova on 2013-05-23
I submitted a bug report:
[https://bugs.launchpad.net/signon-ui/+bug/1183566](https://bugs.launchpad.net/signon-ui/+bug/1183566)

---

### Post by Derek Karpinski on 2013-05-23
```
sudo nano /usr/share/accounts/providers/facebook.provider
```


add this line:
```
<setting name="AllowedSchemes" type="as">['https','http']</setting>
```

right after this line:
```
<group name="user_agent">
```

Save, reboot, login and try adding your facebook account.

Advice being given is to only make this change if you're using a trusted web connection. (you'll be using http instead of https)

---

### Post by Odzinic on 2013-05-24
> **Derek Karpinski said:**
> ```
sudo nano /usr/share/accounts/providers/facebook.provider
```


add this line:
```
<setting name="AllowedSchemes" type="as">['https','http']</setting>
```

right after this line:
```
<group name="user_agent">
```

Save, reboot, login and try adding your facebook account.

Advice being given is to only make this change if you're using a trusted web connection. (you'll be using http instead of https)
This worked. Thanks for the temporary fix.

---

### Post by richierich1986 on 2013-05-27
[FONT=arial]Thanks Derek Karpinksi!

After having logged into Facebook, I removed that line [/FONT]"[COLOR=#000000][FONT=Ubuntu Mono]<setting name="AllowedSchemes" type="as">['https','http']</setting>"
[FONT=arial]again, so the file was like before, and the facebook account still works. So does that mean, with that line removed from the
file, that it's using https again now, instead of the temporary http?[/FONT][/FONT][/COLOR]

---

### Post by SaltyFishPaste on 2013-05-28
Had the same problem and figured this out, so thought I would post my results.

The problem that everyone is happening is due to the Faceboke 'Secure Browsing' option. This requires that Facebook logins and connections use HTTPS, instead of HTTP (secure HTTP vs normal HTTP). By default, I believe online accounts is using HTTP, so this just won't work.

Because of this, we have a couple of options.

**Option 1 (Insecure Solution):**
Disable Facebook Secure browsing through the security interface on Facebook.com. This will disable HTTPS defaults on ALL of your Facebook pages on ALL devices, e.g. cell phones, other computers, etc. This works, but it is not the ideal solution.

[B]Option 2 (Right Way):
[/B]We can simply request that online accounts just use an HTTPS connection, instead of an HTTP connection. To do this, we can use Derek Karpinski's previous advice (quoted below). This is essentially telling Online Accounts to try both HTTP and HTTPS. Since Facebook needs HTTPS, this is what we want. After doing his steps below, delete the Ubuntu app on Facebook (if you had previously tried and failed to add it), log out of Facebook, and close Online Accounts. You actually don't need to restart your computer, just close Online Accounts. Re-open Online Accounts and try again. and things should work fine!

    > 
Re: Ubuntu online accounts - cannot add facebook
    Code:

    sudo nano /usr/share/accounts/providers/facebook.provider


    add this line:
    Code:

    <setting name="AllowedSchemes" type="as">['https','http']</setting>

    right after this line:
    Code:

    <group name="user_agent">


---

### Post by sagara on 2013-05-30
Glad to know this got resolved.  It was annoying the heck out of me.
Kudos to Derek and SaltyFishPaste for explaining the solution.

Will loop in folks from another thread who had the same problem.

---

### Post by AngelOskur0 on 2013-06-05
Thanks! Works perfect! :3

---

### Post by GobbleMonkey on 2013-06-15
Hello. I have accidentally found a way around this problem. What you can do is very simple. First you must go to firefox and google "activate facebook messenger firefox". You will need to activate the facebook messenger on firefox. This will automatically add your facebook profile to ubuntu. 
Hope this helps.

---

### Post by Sciroccogti on 2013-10-19
None of those things helped for me still can not log in to facebook chat in empathy

---

### Post by e_cap on 2013-10-19
```
sudo apt-get purge empathy
```
```
sudo apt-get install mcp-account-manager-goa
```
```
F2 *unity*
```
```
empathy-accounts
```

hope this works!

---

### Post by richardsdma on 2013-10-21
no, it does not work for me.

---

### Post by richardsdma on 2013-10-23
using empathy in ubuntu is a real mess. 
today, i have tried empathy that comes default to debian 7.2......to my surprise, it is working fine! it connects to facebook account. 
i dont understand what is going on....

---

### Post by richardsdma on 2013-10-29
today, i have tried fedora 19 from liveUSB and the empathy seems to work okay, all my accounts are connecting fine (facebook, gmail and yahoo) 
i guess that the problem has something to do with "ubuntu account"

---

