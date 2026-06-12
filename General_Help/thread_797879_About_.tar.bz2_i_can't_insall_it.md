---
title: "About .tar.bz2 i can't insall it"
date: 2008-05-17
forum: General Help
---

### Post by eAi-T0ky0 on 2008-05-17
hey guys ... wat's up today!!! hope fine all :)

i have some problem here ... when i download that firefox-3.0rc1 bec i wanna upgrade my firefox now .. "firefox-3.0rc1.tar.bz2" << i get this

then i Extract it in desktop :KS

it give me folder name "FireFox" and i don't know how to install it .. there nothing in it to can install it can any anybody help me there?? :(

---

### Post by eAi-T0ky0 on 2008-05-17
Some One HELLLLLLLLLLLLLLLLLLLLLLLLLLLP

---

### Post by Gunman1982 on 2008-05-17
That "firefox" directory on the Desktop is the installation of firefox. Open the directory and click on "firefox" then a window should appear with asking you whether to execute or show the file, click on execute.

---

### Post by eAi-T0ky0 on 2008-05-17
there was not any "firefox" installation in the directory firefox in my desktop!!!!

---

### Post by ibuclaw on 2008-05-17
Open the terminal, cd to the location of the extracted content and type in:
```
ls
```
What files are highlighted as [COLOR="Lime"]green[/COLOR]?

Regards
Iain

---

### Post by ibuclaw on 2008-05-17
I've managed to open it successfully...
```

cd ~/Desktop/firefox
./firefox

```

It's the executable text script.

Regards
Iain

---

### Post by eAi-T0ky0 on 2008-05-17
```
eai-tokyo@Ezz:~$ ls /home/eai-tokyo/Desktop/firefox
application.ini             libfreebl3.so    libxul.so
blocklist.xml               libjemalloc.so   modules
browserconfig.properties    libmozjs.so      mozilla-xremote-client
chrome                      libnspr4.so      old-homepage-default.properties
components                  libnss3.so       platform.ini
crashreporter               libnssckbi.so    plugins
crashreporter.ini           libnssdbm3.so    README.txt
crashreporter-override.ini  libnssutil3.so   removed-files
defaults                    libplc4.so       res
dictionaries                libplds4.so      run-mozilla.sh
extensions                  libsmime3.so     searchplugins
firefox                     libsoftokn3.chk  Throbber-small.gif
firefox-bin                 libsoftokn3.so   updater
greprefs                    libsqlite3.so    updater.ini
icons                       libssl3.so
libfreebl3.chk              libxpcom.so
eai-tokyo@Ezz:~$ cd~
bash: cd~: command not found
eai-tokyo@Ezz:~$ cd ~
eai-tokyo@Ezz:~$ cd ~/Desktop/firefox
eai-tokyo@Ezz:~/Desktop/firefox$ ./firefox
eai-tokyo@Ezz:~/Desktop/firefox$ 

```

there nothing done!!!

it still beta :(

---

### Post by Gunman1982 on 2008-05-17
try:
cd ~/Desktop/firefox
chmod +x ./firefox
./firefox

---

### Post by eAi-T0ky0 on 2008-05-17
```
eai-tokyo@Ezz:~$ cd ~/Desktop/firefox
eai-tokyo@Ezz:~/Desktop/firefox$ chmod +x ./firefox
eai-tokyo@Ezz:~/Desktop/firefox$ ./firefox
eai-tokyo@Ezz:~/Desktop/firefox$ 

```

It Open New Windows Of Firefox But It Still Beta :(

---

### Post by Gunman1982 on 2008-05-17
Close all opened firefox windows and try again.

---

### Post by eAi-T0ky0 on 2008-05-17
i do it

and about firefox

Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5

it's still Beta :( :( :(

---

### Post by eAi-T0ky0 on 2008-05-17
HElp Please somebody help :(:(:(:(

---

### Post by bamsan on 2008-05-17
Firefox 3 is indeed still beta. It's not released yet

That's why u get 'rc1' in the version number. It stands for 'release candidate'

---

### Post by petri on 2008-05-18
I finally succeeded thanks to tinivole

```
cd ~/firefox
./firefox
```

(Yes I removed the /Desktop because it didn't kind of a fit in my Ubuntu wich is not in english :)

and now I got "About Firefox" : Mozilla/5.0 (X11; U; Linux i686 
(x86_64); sv-SE; rv:1.9) Gecko/2008051202 Firefox/3.0

So eAi-T0ky0, try with the code above. Maybe it's best to download rc1 again?

But now I have to start 3.0rc1 with Terminal and the code above. How do I change the preferences of the launcher in the program menu?

---

### Post by singetak on 2008-05-18
right click Applications then navigate to the firefox item and double click it.then press the browse button and select firefox file in the firefox directory.

---

### Post by eAi-T0ky0 on 2008-05-18
it won't work with me

HOw Can I INstall Firefox please :(

---

### Post by emshains on 2008-05-18
Just wait for it to be .deb, later put in repos. That's what am doing.

---

### Post by logx on 2008-05-18
Hello,

Firefox 3 still in Beta 5, so you will have to wait for the final release. Not for soon anyway...

---

