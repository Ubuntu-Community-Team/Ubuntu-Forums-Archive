---
title: "Microsoft 365 Account - Online Accounts - Problem"
date: 2024-06-17
forum: General Help
---

### Post by john-jcard on 2024-06-17
Hi,

When I first installed Ubuntu 24.04 I managed to use the Online Accounts section in control panel, to setup a Microsoft 365 Account. This then enabled access to my OneDrive files through the file explorer. After a few hours, it stopped working. I tried to remove the account, and recreate it. I cannot get it to work however. After entering my email address on the Webpage presented (Microsoft login), I just get the following error;

[h=2]We're unable to complete your request[/h]unauthorized_client: The  client does not exist or is not enabled for consumers. If you are the  application developer, configure a new application through the App  Registrations in the Azure Portal at  [https://go.microsoft.com/fwlink/?linkid=2083908](https://go.microsoft.com/fwlink/?linkid=2083908).

I have spent hours searching for a solution, and tried a number of things, including following closely the instructions here;

[https://gitlab.gnome.org/GNOME/gnome-online-accounts/-/wikis/Account-Setup#microsoft-365](https://gitlab.gnome.org/GNOME/gnome-online-accounts/-/wikis/Account-Setup#microsoft-365)

Try as I might, I cannot get this to work.

Apologies if posted in the wrong forum, I couldn't see a more appropriate section. I also couldn't find any previous posts related to this on the forums.

Thanks

---

### Post by QIII on 2024-06-17
Are you saying you are unable to log in just using a browser?

---

### Post by john-jcard on 2024-06-18
No, I can log into Microsoft account normally using a browser. Can access OneDrive etc just fine. It's just when using the online accounts function I have problem. After inputting email address in the prompt from Ubuntu settings, it redirects to a web login to Microsoft and that is where I get the error.

---

### Post by m.banu94 on 2024-06-30
After you finish the process on Microsoft Extra, go back to GNOME Online Accounts remove the Microsoft 365 entry you had than add a new one and input the Client ID of the app you created on Microsoft Extra, than you can proceed with the in-browser sign redirection from Settings, login to your account there, and allow all permissions when prompted in browser and it should work fine

---

