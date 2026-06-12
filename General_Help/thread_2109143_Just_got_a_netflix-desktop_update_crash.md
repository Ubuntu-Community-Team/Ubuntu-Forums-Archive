---
title: "Just got a netflix-desktop update crash"
date: 2013-01-26
forum: General Help
---

### Post by sdowney717 on 2013-01-26
"No apport report written because MaxReports is reached already"

I guess everyone is now broken if they did the update

```
installArchives() failed: Selecting previously unselected package wine-browser-installer.
(Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 318553 files and directories currently installed.)
Unpacking wine-browser-installer (from .../wine-browser-installer_0.6.0~precise_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/wine-browser-installer_0.6.0~precise_amd64.deb (--unpack):
 trying to overwrite '/usr/share/locale/en/LC_MESSAGES/netflix-desktop.mo', which is also in package netflix-desktop 0.5.1~precise
No apport report written because MaxReports is reached already
dpkg-deb (subprocess): subprocess data was killed by signal (Broken pipe)
dpkg-deb: error: subprocess <decompress> returned error exit status 2
Preparing to replace netflix-desktop 0.5.1~precise (using .../netflix-desktop_0.6.0~precise_all.deb) ...
Unpacking replacement netflix-desktop ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for update-notifier-common ...
netflix-desktop: downloading http://developer.netflix.com/files/Netflix_API2_57x57.png
/usr/share/wine-browser-installer/netflix-desktop.install-files: 10: /usr/share/wine-browser-installer/netflix-desktop.install-files: /usr/share/wine-browser-installer/install-files: not found
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/wine-browser-installer_0.6.0~precise_amd64.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: dependency problems prevent configuration of netflix-desktop:
 netflix-desktop depends on wine-browser-installer; however:
  Package wine-browser-installer is not installed.
dpkg: error processing netflix-desktop (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by sdowney717 on 2013-01-26
Went to uninstall it all and do reinstall and can not.
If you update right now, you will break this program

---

### Post by David D. on 2013-01-26
I had this happen on both my 12.10 and Raring Ringtail installs.  One of the error messages I got told me to run "sudo apt-get update" in terminal.  This resulted in instructions in terminal for fixing the update that crashed.  After this process Netflix is working fine in both versions of Ubuntu on my computer.

---

### Post by pompel9 on 2013-01-26
I uninstalled and installed again. I had no problems with installing it again.

---

### Post by generalagony on 2013-01-28
sudo apt-get update
sudo apt-get install -f 

worked for me.

---

### Post by tokkumma on 2013-01-29
am somewhat of a noob, when i last updated netflix, it broke, then i have been doing a bunch of random stuff ppl posted on forums such as these, now i am getting this message(everytime i click on the launcher), any help would be appreciated. (i am running oneiric 11.12)

"Not all of the components required by Project-Id-Version: netflix-desktop
Report-Msgid-Bugs-To: 
POT-Creation-Date: 2013-01-28 19:33-0700
PO-Revision-Date: 2013-01-28 19:33-0700
Last-Translator: Automatically generated
Language-Team: none
Language: en_US
MIME-Version: 1.0
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: 8bit
Plural-Forms: nplurals=2; plural=(n != 1); were downloaded, would you like to download them now? (requires an Internet connection and sudo permissions)"

---

### Post by sdowney717 on 2013-01-29
To solve, I did a com[plete purge uninstall-reinstall, got some odd error, but then it actually ran ok.

---

