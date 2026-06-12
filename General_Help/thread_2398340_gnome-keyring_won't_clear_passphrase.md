---
title: "gnome-keyring won't clear passphrase"
date: 2018-08-10
forum: General Help
---

### Post by cathect2 on 2018-08-10
[COLOR=#242729][FONT=Arial]Under Ubuntu 18.04, gnome-keyring caches PGP passphrases and will retain them, even through logout or reboot. I'm using the program pass to retain my passwords, so I want to be challenged every time I ask pass to show me a password. However, since gnome-keyring retains the password, anyone at my machine can view all of my passwords.

[/FONT][/COLOR]I used dconf-editor to change the gpg-cache-method to "timeout" and the gpg-cache-ttlto 1 second. Then I reset the gnome-keyring daemon with: $ gnome-keyring-daemon -r
[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR][COLOR=#242729][FONT=Arial]However, upon using the passphrase again, it gets cached and will not request the passphrase.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Why is gnome-keyring not honoring these settings? How can I fix this? This is extremely insecure.[/FONT][/COLOR]

---

