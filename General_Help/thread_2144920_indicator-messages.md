---
title: "indicator-messages"
date: 2013-05-13
forum: General Help
---

### Post by garyzw on 2013-05-13
I installed Ubuntu 13.04 about a week ago, at the time i had no need for the mail app in the top panel  so I removed it using the sudo apt-get autoremove indicator-messages command--thinking I could later restore it if needed using the sudo apt-get install indicator-messages command but it did not work. I also had removed Evolution Mail and Calendar as the Evolution mail program crashed while using.

I would like to restore the mail app in the top panel and have it check my gmail--how can this be done?

---

### Post by Frogs Hair on 2013-05-13
What flavor  of Ubuntu ? Thubnderbird is default in Ubuntu , so I am wondering how evolution mail and calendar came to be installed . If you have restarted since installing the indicator try opening the mail client.

---

### Post by garyzw on 2013-05-13
Ubuntu 13.04-- didn't want to use Thunderbird--wanted to use gmail online only. evolution mail and calendar were pre-installed

---

### Post by Frogs Hair on 2013-05-13
Strange, after three 13.04 installations Evolution has not been installed on any of them only Thunderbird . Try installing Tbird  and check the default mail client in the Details Application under Default Applications and open Tbird. For Gmail you may want to check out Unity Mail in the software center. Thunderbird has been default since 11.10. [http://www.omgubuntu.co.uk/2011/05/no-concrete-decision-taken-on-default-ubuntu-mail-app-for-11-10-but-errs-towards-thunderbird](http://www.omgubuntu.co.uk/2011/05/no-concrete-decision-taken-on-default-ubuntu-mail-app-for-11-10-but-errs-towards-thunderbird)

---

### Post by garyzw on 2013-05-13
What I want to do is get the email indicator app back in the top panel and have it default to gmail. See attached picture

[ATTACH=CONFIG]242568[/ATTACH]

---

### Post by Frogs Hair on 2013-05-14
The indicator works by gathering information from and opening the default email client which is Thunderbird unless you are using the Ubuntu-Gnome release of 13.04 . The Gnome release uses Evolution and that is why knowing the Ubuntu flavor is important. Either way you have to install the default email client for the indicator to appear and work. The indicator won't open the web browser and check for mail, but will check the default mail client.

---

### Post by grahammechanical on 2013-05-14
Are you looking for the envelope icon? I do not have that icon in my new 13.04 and that is because I have yet to run and email application or use IRC or anything like that. Once I run an application associated with that email icon then the icon will appear in the to panel.

Have you tried opening Online Accounts in system settings. I see that Google (including Gmail) is listed. Have you set up the account?

Regards.

---

### Post by garyzw on 2013-05-14
> **grahammechanical said:**
> Are you looking for the envelope icon? I do not have that icon in my new 13.04 and that is because I have yet to run and email application or use IRC or anything like that. Once I run an application associated with that email icon then the icon will appear in the to panel.

Have you tried opening Online Accounts in system settings. I see that Google (including Gmail) is listed. Have you set up the account?

Regards.

Yes I set up Gmail with the  Online Accounts--but it seems that as Frogs Hair said it only will notify of mail when using Thunderbird

---

### Post by Frogs Hair on 2013-05-14
> **garyzw said:**
> Yes I set up Gmail with the  Online Accounts--but it seems that as Frogs Hair said it only will notify of mail when using Thunderbird

I tested web apps also and the result was that Firefox opened the Gmail login page which could have been done with a browser shortcut. Unity Mail notifies of new messages in Gmail but it also only opens the web browser to the Gmail login page.

---

### Post by garyzw on 2013-05-14
Thanks all who replied--I will mark it as solved

---

