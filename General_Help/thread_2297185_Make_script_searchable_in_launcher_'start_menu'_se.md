---
title: "Make script searchable in launcher 'start menu' search."
date: 2015-10-01
forum: General Help
---

### Post by jwhitene on 2015-10-01
Ubuntu 15.04 default install

I want to be able to run a custom.sh script by hitting my start menu key (right command key in mac) and searching for the first few letters of it.  

I just tried this:  [http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand](http://askubuntu.com/questions/13758/how-can-i-edit-create-new-launcher-items-in-unity-by-hand)

I copied vim.desktop to ldap.desktop, and edited the file so it contains this:

[Desktop Entry]
Name=Gawor LDAP Editor
GenericName=Ldap Editor
GenericName[de]=ldapeditor
Comment=Edit ldap 
Comment[en_CA]=Edit ldap 
Comment[en_GB]=Edit ldap 
TryExec=/usr/bin/lbe.sh
Exec=/usr/bin/lbe.sh
Terminal=false
Type=Application
Icon=ldap
Categories=Utility;LdapEditor;
StartupNotify=false
MimeType=text/plain;

/usr/bin/lbe.sh is a link to ~/ldap/lbe.sh.   

lrwxrwxrwx 1 root root 32 Oct  1 11:39 /usr/bin/lbe.sh -> /home/blahblah/Gawor-ldap/lbe.sh

If I hit my 'start menu' key and type LDAP, or ldap, or Gawor, or lbe.sh it cannot find it.  Is this not the correct approach, or did I do something wrong?

---

### Post by efflandt on 2015-10-01
Where did you put the ldap.desktop file? System desktop files (owned by root) go in /usr/share/applications/ with 644 permission as root/root. Personal ones go in ~/.local/share/applications/ (with 775 permission as you/yourgroup I guess). To see newly created ones, you have to log out of X and log back in. Maybe that is why you cannot find it if you tried to find it right after creating it.

And if you put it in /usr/share/applications/ not sure how that will work with a symlink to a script in your home directory. Since you are attempting to run a script in your own home, I would suggest trying the .desktop file in ~/.local/share/applications/ pointing directly to the full path of the script in your home. Note that desktop shortcuts do NOT interpret shell meta-characters (like ~/) in Exec=, and sometimes has trouble with parameters, unless you launch it with a shell like: Exec=sh -c 'java -jar ~/Downloads/Minecraft.jar'

Typically you should put any personal scripts or binary programs (or symlinks to them) in ~/bin/ which ends up in your $PATH once you log back into X. Then you could run your scripts by simply typing their name in a terminal window, instead of needing a path or doing a cd first. And you probably would not even need a path to your script in your desktop launcher.

---

### Post by jwhitene on 2015-10-01
I missed that personal ones go into .local.  sudo mv /usr/share/applications/ldap.desktop ~/.local/share/applications/ldap.desktop && chown jwhitene:jwhitene ~/.local/share/applications/ldap.desktop.  Did not have to log out, search found it right way, worked perfectly, thanks.

---

