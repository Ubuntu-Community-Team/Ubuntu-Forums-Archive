---
title: "Downloads Folder Deleted..."
date: 2024-09-26
forum: General Help
---

### Post by wyattwhiteeagle on 2024-09-26
```
   find /home/wyatt/Downloads -type d -empty -delete
```
```
   find /home/wyatt/Downloads/* -type d -empty -delete
```
Why is the first line deleting the Downloads folder and the second line telling me "no such file or directory?"

Not ran at the same time.
I'm using timeshift as a "system restore point".

---

### Post by 1fallen on 2024-09-26
You told it to do that...lol
If I may make a suggestion, use this:
```
rm -rf /home/me/Downloads/{*,.*}
```
That will remove all even hidden in your Download Directory, and not the directory itself.
Proof, I backed my Downloads folder up:
```
ls
Applications                       Documents          krita-5.2.0-x86_64.appimage  Public               umask.sh
ap-sw                              Downloads          KVM-GPU-Passthrough          repo                 Videos
ap-switch                          Downloads.bk       movies                       steam.desktop        vi.txt
ap-sw.sh                           fileperms          mpv-options.txt              system-info-scripit  zc-master
balenaEtcher-1.18.11-x64.AppImage  fstab.git          Music                        Templates
cachyos-repo                       install-linux.sh   New-Vault1.bcup              timeshift
Desktop                            journal.cofig.txt  Pictures                     umasaksystem.sh

```
Now I'll add a big folder to that
```
ls Downloads
```
Nothing there yet, So I'll load it with some:
```
 ls Downloads
160115-bDMZT.tar.tar  balena-etcher_1.18.4_amd64.deb  bookmarks-to-json-main.zip
9dt19z.7z             bookmarks-2024-04-22.json       refind-flashdrive-0.12.0

```
Now with my suggested code:
```
&#9492;&#9472;> rm -rf /home/me/Downloads/{*,.*}
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> ls Downloads
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> 

```
Or
```
[FONT=monospace][COLOR=#000000]find /home/me/Downloads && rm -rf /home/me/Downloads/{*,.*} [/COLOR]
/home/me/Downloads 
/home/me/Downloads/brscan3-0.2.13-1.amd64.deb 
/home/me/Downloads/cachyos-desktop-linux-240714.iso 
/home/me/Downloads/cachyos-wallpapers-develop.zip 
/home/me/Downloads/CSI_Linux_2023.2_QCOW2.7z.torrent 
/home/me/Downloads/davinci-resolve-checker-master.zip 
/home/me/Downloads/davinci.png 
/home/me/Downloads/dwagent.sh


[/FONT]
```
Or less verbose:
```
[FONT=monospace][COLOR=#000000]find /home/me/Downloads -type d -empty && rm -rf /home/me/Downloads/{*,.*}[/COLOR]

[/FONT]
```
And I still have my Download Directory.

> **ACTIONS**
    -delete
           Delete  files;  true if removal succeeded.  If the removal failed, an error message is issued.  If
           **-delete** fails, **find**'s exit status will be nonzero (when it  eventually  exits).   Use  of  **-delete**
           automatically turns on the **-depth** option.

           **Warnings**:  Don't  forget  that  the  find  command  line is evaluated as an expression, so putting
           **-delete** first will make **find** try to delete everything below the  starting  points  you  specified.
           When  testing a **find** command line that you later intend to use with **-delete**, you should explicitly
           specify **-depth** in order to avoid later surprises.  Because  **-delete**  implies  **-depth**,  you  cannot
           usefully use **-prune** and **-delete** together.

---

### Post by TheFu on 2024-09-27
When a command doesn't work the way you think, you can help yourself by running that command through "explainshell", which is a website.  It will pull up the relevant parts of the manpage for the command.  In this case, you've told it to only look for directories (-type d) so files and links will be ignored.  

No need to post for help here for stuff like this.

---

