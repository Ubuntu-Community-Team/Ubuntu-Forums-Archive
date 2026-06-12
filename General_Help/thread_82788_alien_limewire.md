---
title: "alien limewire"
date: 2005-10-27
forum: General Help
---

### Post by christian on 2005-10-27
I downloaded limewire basic, installed alien, ran these two commands from the directory:

sudo alien -d LimeWireLinux.rpm
sudo dpkg -i limewire-free_4.9.23-1_i386.deb


once it's finished how do i actually get limewire to run- I point smeg to the limewire file in /usr/bin/limewire but it doesn't work...

Thanks!
Christian

---

### Post by jeffreyvergara.NET on 2005-10-27
I used [www.ubuntuguide.org](www.ubuntuguide.org) when installing Limewire, I didnt encounter any problem installing and running... you can also use Automatix

---

### Post by christian on 2005-10-27
i used the guide at first- installing both java sun and limewire, but when I clicked on limewire to run the startup limewire splash screen comes up saying 'loading resources.." but then another window pops up saying java.lang java.lang.NoClassDefFoundError ... etc, etc

noone seemed to have an answer as to how to deal with that issue so I tried using alien to install it- but there seems to be no waying to get limewire to execute using it...

if you know how to solve either of these issues I'd be most grateful!

thanks!
christian

---

### Post by Pablo_Escobar on 2005-10-27
First of all. Go to terminal type "lime" and then press TAB key. It should autocomplete the Limewire command, and show You how the program in bin is really called (I believe it's Limewire-free or something). 
If it doesn't work try "Lime" and TAB key in terminal - autocomplete is case sensitive.

---

### Post by sumanjay on 2005-11-08
To solve the problem of running limewire, you need SMEG to point to this link - /usr/bin/runLime.sh

I might be wrong, but I think your PATH variable hasn't been setup properly, which in turn might be due to a bad sun-java installation. The error "java.lang java.lang.NoClassDefFoundError" normally occurs when the JRE is unable to find the path to your application's classes. Try re-installing the JRE currently on your system, then try "sudo apt-get limewire-free".

---

### Post by Trab on 2005-11-08
i used Alien as well...
i dunno what the -d option does...
after doing sudo dpkg -i limewire_blah.deb u need to run the command 
```
 
limewire

```
go figure huh?
u can also add it via smeg to ur menu... i think if u 
```

killall gnome-panel

```
it should auto add.... if not hit ctrl+F2 and type limewire.
gl

---

### Post by sumanjay on 2005-11-08
Trab, the "-d" option in alien builds a debian (also Ubuntu's native) package. Alien can also be used to build rpm(s), Solaris pkg(s) and a few other package formats. Debian packages are built by default on Ubuntu. 

I doubt if running "limewire" will execute the app properly as Limewire's website mentions that the script "runLime.sh" should be executed to startup the app.

---

### Post by Andyfield123 on 2007-05-10
if you go to limewire.com there is an option that says ubuntu next to it.
This should install using the GDebi Package Installer.

---

