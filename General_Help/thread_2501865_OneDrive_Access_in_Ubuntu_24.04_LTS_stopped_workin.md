---
title: "OneDrive Access in Ubuntu 24.04 LTS stopped working"
date: 2024-10-23
forum: General Help
---

### Post by johan_vm on 2024-10-23
In Ubuntu 24.04 Gnome/Nautilus, I logged in to my OneDrive account.
([https://www.omgubuntu.co.uk/2024/04/set-up-onedrive-file-access-in-ubuntu](https://www.omgubuntu.co.uk/2024/04/set-up-onedrive-file-access-in-ubuntu))

This has been working great: upload, download, view files, ...
All of a sudden this stopped working.
I still see every folder and every file in my Onedrive, but I'm not able to open files.
When I try to open a photo, I get an error:

```
Can't open image - HTTP-error: Unauthorized
```

When I try to open a DOCX file, LibreOffice doesn't show the actual Word Document.
It shows an empty Word document with this content:
```
{"error":{"code":"unauthenticated","message":"Unauthenticated"}}
```

Any ideas on how to solve this?
I already tried removing and re-adding my Microsoft account.

I'm not using third party software.  Just Ubuntu 24.04 + Gnome Shell 46.0 + Nautilus 46.02.

---

### Post by johan_vm on 2024-10-30
Apparently nobody on this forum knows how to solve or investigate this.
Any ideas where I can get help with this issue?

---

### Post by 1fallen on 2024-10-30
Take a look here it is a known bug: [https://serverhost.com/blog/solving-onedrive-file-access-issues-in-ubuntu-24-04-a-practical-guide/](https://serverhost.com/blog/solving-onedrive-file-access-issues-in-ubuntu-24-04-a-practical-guide/)

---

### Post by johan_vm on 2024-10-31
Thank you for helping me.
Unfortunately, I think my problem is not the same.
When I edit ~/.config/goa-1.0/accounts.conf, there is no [Invalid UTF-8] in this file.
My client ID is already present in OAuth2ClientId andOAuth2RedirectUri.

---

### Post by johan_vm on 2024-10-31
For future reference: if someone might encounter the same error:
I created an issue one Gnome's Gitlab: [https://gitlab.gnome.org/GNOME/gnome-online-accounts/-/issues/382](https://gitlab.gnome.org/GNOME/gnome-online-accounts/-/issues/382)
I'll try to post the solution here whenever I find one.

---

### Post by johan_vm on 2024-11-01
As promised: I found a solution, thanks to the help I got on Gnome's Gitlab.
Ubuntu and Mint users encountered this bug.
Updating **libmsgraph-0-1** solved this issue.
Ubuntu 24.04 uses version [0.2.1-0ubuntu3]("https://answers.launchpad.net/ubuntu/noble/amd64/libmsgraph-0-1").
I downloaded and installed version [0.2.3-1]("https://launchpad.net/ubuntu/oracular/amd64/libmsgraph-0-1"), and the bug was gone.

---

### Post by mierenneuker on 2024-11-18
I realise this is probably a stupid question but please could you provide the steps to download and install the 0.2.3-1 version as my knowledge of this is very limited

---

### Post by christer08 on 2024-12-02
I am in the same situation as mierenneuker.
Maybe this issue will be solved in a coming official update? If not I am interested in some guide, how to download and install [B]libmsgraph-0-1.

I managed to solve this by myself! 
To download: 
[/B][https://launchpad.net/ubuntu/oracular/amd64/libmsgraph-0-1/0.2.3-1](https://launchpad.net/ubuntu/oracular/amd64/libmsgraph-0-1/0.2.3-1)
  Click on the file on the right-handside, and choose "save"
  The file will be saved in your Downloads folder

Open  [https://ubuntu.com/server/docs/package-management](https://ubuntu.com/server/docs/package-management)
Look for  
[h=3][Installing a deb file]("https://ubuntu.com/server/docs/package-management#installing-a-deb-file")[/h]run the command:

christer@christer-Latitude-5480:~/Downloads$ sudo dpkg -i libmsgraph-0-1_0.2.3-1_amd64.deb
(Reading database ... 207704 files and directories currently installed.)
Preparing to unpack libmsgraph-0-1_0.2.3-1_amd64.deb ...
Unpacking libmsgraph-0-1:amd64 (0.2.3-1) over (0.2.1-0ubuntu3) ...
Setting up libmsgraph-0-1:amd64 (0.2.3-1) ...
Processing triggers for libc-bin (2.39-0ubuntu8.3) ...
christer@christer-Latitude-5480:~/Downloads$ 

After reboot, it works!

---

