---
title: "Fontconfig setup corrupts file system (read-only)"
date: 2015-08-22
forum: General Help
---

### Post by Mortesins93 on 2015-08-22
Hello,

I've had some weird problems with ubuntu 14.04.2 these last days and I was about to open a thread asking for help but it seems I solved the problem (at least for now), but I decided to write it anyways so that it could be a reference just in case someone else runs into the same problem.
So basically what happened was that anytime I tried installing something with apt-get that would trigger the ***fontconfig*** triggers, I'd get the following error with a resulting read-only filesystem:
```
Setting up fontconfig (2.11.0-0ubuntu4.1) ...
Regenerating fonts cache... failed.
See /var/log/fontconfig.log for more information.
touch: cannot touch '/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
sh: 1: cannot create /var/lib/update-notifier/updates-available: Read-only file system
E: Sub-process /usr/bin/dpkg returned error code (2)
E: Problem executing scripts DPkg::Post-Invoke 'if [ -d /var/lib/update-notifier]; then touch /var/lib/update-notifier/dpkg-run-stamp; fi; if [ -e /var/lib/update-notifier/updates-available ]; then echo > /var/lib/update-notifier/updates-available; fi '
E: Sub-process returned an error code.
```
At first I thought the read-only filesystem was the problem but then, after fixing it by running the following command on a liveCD:
```
sudo e2fsck -C0 -f -y -v /dev/sda5 
```
(where /dev/sda5 is the partition of the root filesystem for my ubuntu 14.04.2 install), I noticed that the filesystem actually became read-only because of the fontconfig errors. In other words, after doing the filesystem repair with the previous command, everything went back to normal until I ran the install command again, which would cause the filesystem to go back to read-only.
So, since I figured out the problem was fontconfig, I read the log and found that the last two lines were as follows:
```
/usr/share/texmf/fonts/opentype/public/lm-math: caching, new cache contents: 1 fonts, 0 dirs
/usr/share/texmf/fonts/opentype/public/tex-gyre:
```
And the last line did not even have a newline character at the end, so I guessed the problem was the tex-gyre package. By removing it I seem to have solved the problem.
To be honest, I did not only remove tex-gyre but everything I installed concerning tex:
```
texlive-font-utils texlive-generic-recommended texlive-lang-english texlive-lang-italian texlive-latex-base texlive-latex-base-doc texlive-latex-extra texlive-latex-extra-doc texlive-latex-recommended texlive-latex-recommended-doc texlive-luatex texlive-pictures tex-common texlive-pictures-doc tex-gyre texlive-pstricks texinfo texlive-pstricks-doc texlive-base texmaker texlive-binaries texmaker-data texlive-extra-utils texworks texlive-fonts-recommended texworks-help-en texlive-fonts-recommended-doc
```
and also the package with windows fonts:
```
ttf-mscorefonts-installer
```
even though after doing it, it's pretty safe to say it would have worked too if I only removed tex-gyre.
By the way, after fontconfig failed, I could not run any apt-get commands because I got an error saying I had to run:
```
sudo dpkg --configure -a
```
but if I ran that command, I would resetup fontconfig which would lead to the same error causing the file system to go in read-only mode. So what I did, in order to be able to run any apt-get command, is removed fontconfig with dpkg:
```
sudo dpkg -r fontconfig
```
After running this command I was able to run:
```
sudo apt-get remove tex-gyre
```
which solved the problem.

---

