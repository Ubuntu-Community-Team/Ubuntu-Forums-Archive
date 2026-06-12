---
title: "locale: Kann LC_ALL nicht auf die Standard-Lokale einstellen: Datei oder Verzeichnis"
date: 2017-06-07
forum: General Help
---

### Post by alexander-skwar on 2017-06-07
[FONT=arial]Hello[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Since about a week or two agao, [FONT=lucida console]perl[/FONT] and other programs show error messages like the following:[/FONT]


```

[FONT=arial]perl: warning: Setting locale failed.[/FONT]
[FONT=arial]perl: warning: Please check that your locale settings:[/FONT]
[FONT=arial]    LANGUAGE = "de_DE",[/FONT]
[FONT=arial]    LC_ALL = (unset),[/FONT]
[FONT=arial]    LC_IDENTIFICATION = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_TIME = "en_US",[/FONT]
[FONT=arial]    LC_NUMERIC = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_PAPER = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_MEASUREMENT = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_ADDRESS = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_MONETARY = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_NAME = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LC_TELEPHONE = "de_CH.UTF-8",[/FONT]
[FONT=arial]    LANG = "de_CH.UTF-8"[/FONT]
[FONT=arial]    are supported and installed on your system.[/FONT]
[FONT=arial]perl: warning: Falling back to a fallback locale ("de_CH.UTF-8").[/FONT]

```
[FONT=arial]
[/FONT]
[FONT=arial]That's just a tiny wee bit annoying… And I don't have the slightest clue, what I might have misconfigured on my Gnome Ubuntu 16.04 system. Let me send along output of a few programs.[/FONT]
[FONT=arial]
[/FONT][FONT=arial]
**locale**[/FONT]
[FONT=arial]
[/FONT]
```

[FONT=arial]$ locale[/FONT]
[FONT=arial]locale: Kann LC_ALL nicht auf die Standard-Lokale einstellen: Datei oder Verzeichnis nicht gefunden[/FONT]
[FONT=arial]LANG=de_CH.UTF-8[/FONT]
[FONT=arial]LANGUAGE=de_DE[/FONT]
[FONT=arial]LC_CTYPE="de_CH.UTF-8"[/FONT]
[FONT=arial]LC_NUMERIC=de_CH.UTF-8[/FONT]
[FONT=arial]LC_TIME=en_US[/FONT]
[FONT=arial]LC_COLLATE="de_CH.UTF-8"[/FONT]
[FONT=arial]LC_MONETARY=de_CH.UTF-8[/FONT]
[FONT=arial]LC_MESSAGES="de_CH.UTF-8"[/FONT]
[FONT=arial]LC_PAPER=de_CH.UTF-8[/FONT]
[FONT=arial]LC_NAME=de_CH.UTF-8[/FONT]
[FONT=arial]LC_ADDRESS=de_CH.UTF-8[/FONT]
[FONT=arial]LC_TELEPHONE=de_CH.UTF-8[/FONT]
[FONT=arial]LC_MEASUREMENT=de_CH.UTF-8[/FONT]
[FONT=arial]LC_IDENTIFICATION=de_CH.UTF-8[/FONT]
[FONT=arial]LC_ALL=[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]language packages[/FONT]**
[FONT=arial]
[/FONT]
```

[FONT=arial]$ dpkg -l | grep 'ii  language'[/FONT]
[FONT=arial]ii  language-pack-de                                            1:16.04+20160627                              all          translation updates for language German[/FONT]
[FONT=arial]ii  language-pack-de-base                                       1:16.04+20160627                              all          translations for language German[/FONT]
[FONT=arial]ii  language-pack-en                                            1:16.04+20161009                              all          translation updates for language English[/FONT]
[FONT=arial]ii  language-pack-en-base                                       1:16.04+20160627                              all          translations for language English[/FONT]
[FONT=arial]ii  language-pack-gnome-de                                      1:16.04+20160627                              all          GNOME translation updates for language German[/FONT]
[FONT=arial]ii  language-pack-gnome-de-base                                 1:16.04+20160627                              all          GNOME translations for language German[/FONT]
[FONT=arial]ii  language-pack-gnome-en                                      1:16.04+20161009                              all          GNOME translation updates for language English[/FONT]
[FONT=arial]ii  language-pack-gnome-en-base                                 1:16.04+20160627                              all          GNOME translations for language English[/FONT]
[FONT=arial]ii  language-pack-gnome-nds                                     1:16.04+20160627                              all          GNOME translation updates for language German, Low[/FONT]
[FONT=arial]ii  language-pack-gnome-nds-base                                1:16.04+20160627                              all          GNOME translations for language German, Low[/FONT]
[FONT=arial]ii  language-pack-nds                                           1:16.04+20160627                              all          translation updates for language German, Low[/FONT]
[FONT=arial]ii  language-pack-nds-base                                      1:16.04+20160627                              all          translations for language German, Low[/FONT]
[FONT=arial]ii  language-selector-common                                    0.165.4                                       all          Language selector for Ubuntu[/FONT]
[FONT=arial]ii  language-selector-gnome                                     0.165.4                                       all          Language selector for Ubuntu[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]~/.profile[/FONT]**
[FONT=arial]
[/FONT]
```

[FONT=arial]$ cat .profile [/FONT]
[FONT=arial]# ~/.profile: executed by the command interpreter for login shells.[/FONT]
[FONT=arial]# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login[/FONT]
[FONT=arial]# exists.[/FONT]
[FONT=arial]# see /usr/share/doc/bash/examples/startup-files for examples.[/FONT]
[FONT=arial]# the files are located in the bash-doc package.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# the default umask is set in /etc/profile; for setting the umask[/FONT]
[FONT=arial]# for ssh logins, install and configure the libpam-umask package.[/FONT]
[FONT=arial]#umask 022[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# if running bash[/FONT]
[FONT=arial]if [ -n "$BASH_VERSION" ]; then[/FONT]
[FONT=arial]    # include .bashrc if it exists[/FONT]
[FONT=arial]    if [ -f "$HOME/.bashrc" ]; then[/FONT]
[FONT=arial]    . "$HOME/.bashrc"[/FONT]
[FONT=arial]    fi[/FONT]
[FONT=arial]fi[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]# set PATH so it includes user's private bin directories[/FONT]
[FONT=arial]PATH="$HOME/bin:$HOME/.local/bin:$PATH"[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]dpkg-reconfigure locales[/FONT]**
[FONT=arial]
[/FONT]
[FONT=arial]I ran the following:[/FONT]
[FONT=arial]
[/FONT]
```

[FONT=arial]sudo dpkg-reconfigure locales[/FONT]

```
[FONT=arial]
[/FONT]
[FONT=arial]But this didn't change anything &#9785;[/FONT]
[FONT=arial]
[/FONT]
**[FONT=arial]locale-gen[/FONT]**
[FONT=arial]
[/FONT]
```

[FONT=arial]$ sudo locale-gen[/FONT]
[FONT=arial]Generating locales (this might take a while)...[/FONT]
[FONT=arial]  de_AT.UTF-8... done[/FONT]
[FONT=arial]  de_BE.UTF-8... done[/FONT]
[FONT=arial]  de_CH.ISO-8859-1... done[/FONT]
[FONT=arial]  de_CH.UTF-8... done[/FONT]
[FONT=arial]  de_DE.ISO-8859-1... done[/FONT]
[FONT=arial]  de_DE.UTF-8... done[/FONT]
[FONT=arial]  de_DE.ISO-8859-15@euro... done[/FONT]
[FONT=arial]  de_LI.UTF-8... done[/FONT]
[FONT=arial]  de_LU.UTF-8... done[/FONT]
[FONT=arial]  en_AG.UTF-8... done[/FONT]
[FONT=arial]  en_AU.UTF-8... done[/FONT]
[FONT=arial]  en_BW.UTF-8... done[/FONT]
[FONT=arial]  en_CA.UTF-8... done[/FONT]
[FONT=arial]  en_DK.UTF-8... done[/FONT]
[FONT=arial]  en_GB.UTF-8... done[/FONT]
[FONT=arial]  en_HK.UTF-8... done[/FONT]
[FONT=arial]  en_IE.UTF-8... done[/FONT]
[FONT=arial]  en_IN.UTF-8... done[/FONT]
[FONT=arial]  en_NG.UTF-8... done[/FONT]
[FONT=arial]  en_NZ.UTF-8... done[/FONT]
[FONT=arial]  en_PH.UTF-8... done[/FONT]
[FONT=arial]  en_SG.UTF-8... done[/FONT]
[FONT=arial]  en_US.UTF-8... done[/FONT]
[FONT=arial]  en_ZA.UTF-8... done[/FONT]
[FONT=arial]  en_ZM.UTF-8... done[/FONT]
[FONT=arial]  en_ZW.UTF-8... done[/FONT]
[FONT=arial]  nds_DE.UTF-8... done[/FONT]
[FONT=arial]  nds_NL.UTF-8... done[/FONT]
[FONT=arial]Generation complete.[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]/etc/environment[/FONT]**
[FONT=arial]
[/FONT]
```

[FONT=arial]$ cat /etc/environment[/FONT]
[FONT=arial]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]/etc/default/locale[/FONT]**
[FONT=arial]
[/FONT]
```

[FONT=arial]$ cat /etc/default/locale[/FONT]
[FONT=arial]LANG=de_CH.UTF-8[/FONT]
[FONT=arial]#LANGUAGE="de_CH:de"[/FONT]
[FONT=arial]LC_TIME=en_US[/FONT]

```
[FONT=arial]
[/FONT]
**[FONT=arial]Restart[/FONT]**
[FONT=arial]
[/FONT]
[FONT=arial]The problem persists even after a reboot.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Well… Would anyone maybe have an idea?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Thanks,[/FONT]
[FONT=arial]Alexander[/FONT]

---

