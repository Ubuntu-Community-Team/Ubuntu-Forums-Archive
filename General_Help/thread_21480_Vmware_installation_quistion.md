---
title: "Vmware installation quistion"
date: 2005-03-22
forum: General Help
---

### Post by Patrick on 2005-03-22
I'm installing VMware and i get a little bit stuck.

i get this mesage

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.



What do i do  :roll:

---

### Post by bored2k on 2005-03-22
[QUOTE=Patrick]I'm installing VMware and i get a little bit stuck.

i get this mesage

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

The path "/usr/src/linux/include" is not an existing directory.



What do i do  :roll:[/QUOTE]
 You need to  download linux headers for your kernel from apt .

---

### Post by Patrick on 2005-03-22
[QUOTE=bored2k]You need to  download linux headers for your kernel from apt .[/QUOTE]

ahhaa, mkay.

thx bored!

---

### Post by StacyWebb on 2005-03-22
sudo apt-get install linux*
this should get you everything

or just
sudo apt-get install linux-header*
if you just want the headers

---

### Post by Patrick on 2005-03-22
[QUOTE=StacyWebb]sudo apt-get install linux*
this should get you everything

or just
sudo apt-get install linux-header*
if you just want the headers[/QUOTE]

I installed this headers linux-headers-2.6.11-1-686

Rebooted,

Did the VMware installation again and there it came again .

The path "/usr/src/linux/include" is not an existing directory.

Did again the headers thing to check if it was installed ok, and it was 

linux-headers-2.6.11-1-686 is already the newest version

---

### Post by StacyWebb on 2005-03-22
cd /usr/src
what does it say there?

 if you do not see linux as a directory there you may need to do the following

sudo ln -s linux-headers<what every your number is> linux

this will make a linux directory for you
also after this you may need to cd into the linux directory and run the following
make
sudo make install

this should build eveything that you need.

---

### Post by Patrick on 2005-03-22
[QUOTE=StacyWebb]cd /usr/src
what does it say there?

 if you do not see linux as a directory there you may need to do the following

sudo ln -s linux-headers<what every your number is> linux

this will make a linux directory for you
also after this you may need to cd into the linux directory and run the following
make
sudo make install

this should build eveything that you need.[/QUOTE]

patrick@ubuntu:/usr/src/linux-headers-2.6.11-1$ sudo make
  CHK     include/linux/version.h
  UPD     include/linux/version.h
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2

---

### Post by StacyWebb on 2005-03-22
you need to be in 
cd /usr/src/linux
then run 
make
sudo make install

---

### Post by Patrick on 2005-03-22
[QUOTE=StacyWebb]you need to be in 
cd /usr/src/linux
then run 
make
sudo make install[/QUOTE]

if i do sudo ln -s linux-headers-2.6.11-1 linux then there's no folder called linux..........

Maybe i do it trough root terminal???

---

### Post by StacyWebb on 2005-03-22
should work through root terminal
try and let us know what happens

you can also try synaptic to redownload the headers (this will auto install where it needs to go)

---

### Post by Patrick on 2005-03-22
[QUOTE=StacyWebb]should work through root terminal
try and let us know what happens

you can also try synaptic to redownload the headers (this will auto install where it needs to go)[/QUOTE]

Thats what i did ( the synaptic ) but that was no suc6 

I go try the root terminal

Trough rootterminal also no suc6

root@ubuntu:/usr/src # cd linux-headers-2.6.11-1-686
root@ubuntu:/usr/src/linux-headers-2.6.11-1-686 # make
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2
root@ubuntu:/usr/src/linux-headers-2.6.11-1-686 #


If i go to /usr/etc trough filebrowser is see to folders linux-headers-2.6.11-1 and linux-headers 2.6.11-1-686. But no normal linux folder....

I did a apt-get upgrade and then the old headers were downloaded again, the 2.6.10 and something.....

 ](*,)  i feel lost  :|

---

### Post by cdhotfire on 2005-03-25
ya i get this same error.  :-k

---

### Post by ftvcs on 2005-04-13
I got te same problem, but i found a solution:
as root i did:

```
apt-get install linux-headers-2.6.10-5-386
```

and then entered on the vmware installation:

```
/usr/src/linux-headers-2.6.10-5-386/include
```

I hope this helps some of you.

---

### Post by corefile on 2005-04-16
if you have the correct headers installed all you have to do is create a symlink for the missing /usr/src/linux


for instance for me

in the /usr/src directory I did:

ln -s linux-headers-2.6.10-5-k7/ linux

and every thing was fine after that.

---

