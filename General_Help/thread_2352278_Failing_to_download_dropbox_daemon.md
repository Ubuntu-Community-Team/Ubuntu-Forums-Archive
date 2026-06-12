---
title: "Failing to download dropbox daemon"
date: 2017-02-11
forum: General Help
---

### Post by michal-dybczak on 2017-02-11
It doesn't matter how I install drobobox (deb from official site, ppa from older ubuntu version or other) I end up with the same problem. I get windows:

[ATTACH=CONFIG]273644[/ATTACH][ATTACH=CONFIG]273645[/ATTACH]



No, I don't have proxy, Internet connection is fine. No idea what to do next. I never had issues to install dropbox on any other distro. I tried looking for a solution on google, but I found nothing helpful.

P.S. By the way, I see no way to add pictures here, when I use Insert Image option, it's just shows broken image icon.

---

### Post by howefield on 2017-02-11
Do you have the folders ~/.dropbox and ~/.dropbox-dist ?

If so try removing/renaming them and retry the daemon download.

PS. Images can be added with the paperclip icon from the Advanced editor (but not the quick reply option).

---

### Post by michal-dybczak on 2017-02-11
> **howefield said:**
> Do you have the folders ~/.dropbox and ~/.dropbox-dist ?

If so try removing/renaming them and retry the daemon download.

PS. Images can be added with the paperclip icon from the Advanced editor (but not the quick reply option).

No, I don't have those directories. Installation never got around to create them,

New informations:

When launching dropbox from terminal by "dropbox start -i" I get:

```
Starting Dropbox...<urlopen error [SSL: CERTIFICATE_VERIFY_FAILED] certificate verify failed (_ssl.c:590)>
```

I tried updating certificates or add new root certificates, no change, issue persists.

---

### Post by slickymaster on 2017-02-11
*Thread moved to **General Help**.*

---

### Post by Perfect Storm on 2017-02-11
Found a solution for you here: [http://askubuntu.com/questions/787138/cant-install-dropbox-after-upgrading-to-16-04-lts](http://askubuntu.com/questions/787138/cant-install-dropbox-after-upgrading-to-16-04-lts)

---

### Post by michal-dybczak on 2017-02-11
Update:

I tried solution from here:

[https://www.dropboxforum.com/t5/Installation-and-desktop-app/Dropbox-Ubuntu-Install-Update-SSL-Error/m-p/205616#M42370](https://www.dropboxforum.com/t5/Installation-and-desktop-app/Dropbox-Ubuntu-Install-Update-SSL-Error/m-p/205616#M42370)

But when using "cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -" I got:

```
--2017-02-11 18:18:42--  https://www.dropbox.com/download?plat=lnx.x86_64
Translacja www.dropbox.com (www.dropbox.com)... 162.125.66.1
&#321;&#261;czenie si&#281; z www.dropbox.com (www.dropbox.com)|162.125.66.1|:443... po&#322;&#261;czono.
&#379;&#261;danie HTTP wys&#322;ano, oczekiwanie na odpowied&#378;... 302 Found
Lokalizacja: https://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-19.4.13.tar.gz [pod&#261;&#380;anie]
--2017-02-11 18:18:43--  https://dl-web.dropbox.com/u/17/dropbox-lnx.x86_64-19.4.13.tar.gz
Translacja dl-web.dropbox.com (dl-web.dropbox.com)... 162.125.66.6
&#321;&#261;czenie si&#281; z dl-web.dropbox.com (dl-web.dropbox.com)|162.125.66.6|:443... po&#322;&#261;czono.
B&#321;&#260;D: b&#322;&#261;d kontroli certyfikatu dla dl-web.dropbox.com, wystawionego przez `CN=war_ct_sh,OU=CT,O=Orange,L=Warsaw,ST=Warsaw,C=PL':
  Napotkano samodzielnie podpisany certyfikat.
    B&#321;&#260;D: nazwa w certyfikacie `war_ct_sh' nie pasuje do &#380;&#261;danej nazwy hosta `dl-web.dropbox.com'.
Aby po&#322;&#261;czy&#263; si&#281; z dl-web.dropbox.com w sposób niebezpieczny, mo&#380;na u&#380;y&#263; `--no-check-certificate'.

gzip: stdin: unexpected end of file
tar: Child returned status 1
tar: Error is not recoverable: exiting now
```


It seems that there is a problem with polish certificate and I do use ubuntu with Polish locale settings. I am not familiar with certificates. What can I do to fix this?

EDIT": tried to check certificates in /etc/ca-certificates.conf but there is so many of then and names don't point to the polish one. Tried to google how to find specific certificates, who issues them, etc. No luck. Tried to google certain phrases like war_ct_sh or anything that would help me to identify the certificate - nothing. It seems like I was the only person on the whole world with this problem... It's incredibly frustrating because ubuntu always has some issue that is impossible to work on. I tried many times and Ubuntu fails to work normally every time :(. I tried many other distros and it feels like Ubuntu was the worst and most buggy one. It just won't work on my old lenovo laptop, no matter what I do.

---

### Post by michal-dybczak on 2017-02-11
Without dropbox using of this system is pointless for me. So I decided to reinstall ubuntu.
Here is what I did:

1. Installed system.
2. Updated whole system, rebooted.
3. Installed synaptic.
4. Found nautilus-dropbox and installed it.

The same problem.... **I am done with Ubuntu.**

This laptop cannot run ubuntu for a life. And yes, I checked sums, I re-downloaded ubunty many times to get the newest install iso, always the same issues. It just won't work well on this computer. No matter if I like unity, I just can't have any ubuntu or even ubuntu derivatives (like mint) on this lenovo G 780 laptop. Fans are spinning like crazy, battery has a short life, nvidia doesn't work, bumblebee doesn't work, prime doesn't work and dropbox doesn't work. Too many issues :(. On the other hand, arch based systems work well, no issues with nvidia, battery and so on...

Thanks to all who wanted to help, but this machine is simply ubuntu-incompatible.

---

