---
title: "No sound in xubuntu 14.04, dell vostro 3300"
date: 2014-09-10
forum: General Help
---

### Post by christoph5 on 2014-09-10
hello my sound doesent work at all, i have tried link every method that is by googling that the sound doesent work etc, im on xubuntu 14.04 btw, what can i do?? the music seem to show that it plays inside sound settings while theres not coming sounds from speakers on my laptop at all , my laptop is a dell vostro 3300

---

### Post by christoph5 on 2014-09-10
how do i delete my original sound driver and reinstall a updated one please

---

### Post by christoph5 on 2014-09-11
tell me??
HOW ? ?? HOW ?? HOW???

---

### Post by christoph5 on 2014-09-11
you everybody doesent know nothing about linux

---

### Post by christoph5 on 2014-09-15
anything u can do to help me with this output pleae now?? then
> kris@OKOK1:~$ cat /proc/asound/{version,cards,devices,hwdep,pcm,seq/clients}; sudo rm /etc/asound.conf; sudo rm -r ~/.pulse ~/.asound* ;sudo rm ~/.pulse-cookie; sudo apt-get update; sudo apt-get install aptitude; sudo aptitude install paman gnome-alsamixer libasound2-plugins padevchooser libsdl1.2debian-pulseaudio; sudo lshw -short;ls -lart /dev/snd;  cat /dev/sndstat; lspci -nn; lsusb; sudo which alsactl; sudo fuser -v /dev/dsp /dev/snd/* ; dpkg -S bin/slmodemd; dmesg | egrep 'EMU|probe|emu|ALSA|alsa|ac97|udi|snd|ound|irmware'; sudo /etc/init.d/sl-modem-daemon status; sudo grep model /etc/modprobe.d/* ; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; lsmod | egrep 'snd|usb|midi|udio'; pacmd list-sinks; aplay -l; sudo alsa force-reload;  ubuntu-support-status ; sudo lshw -C sound
Advanced Linux Sound Architecture Driver Version k3.13.0-35-generic.
 0 [MID            ]: HDA-Intel - HDA Intel MID
                      HDA Intel MID at 0xfbc00000 irq 48
  1:        : sequencer
  2: [ 0- 0]: digital audio playback
  3: [ 0- 0]: digital audio capture
  4: [ 0- 0]: hardware dependent
  5: [ 0]   : control
 33:        : timer
00-00: HDA Codec 0
00-00: 92HD81B1X5 Analog : 92HD81B1X5 Analog : playback 1 : capture 1
Client info
  cur  clients : 1
  peak clients : 1
  max  clients : 192

Client   0 : "System" [Kernel]
  Port   0 : "Timer" (Rwe-)
  Port   1 : "Announce" (R-e-)
Client  14 : "Midi Through" [Kernel]
  Port   0 : "Midi Through Port-0" (RWe-)
[sudo] password for kris: 
Feil. Prøv igjen.
[sudo] password for kris: 
rm: klarte ikke å fjerne «/etc/asound.conf»: Ingen slik fil eller filkatalog
rm: klarte ikke å fjerne «/home/kris/.pulse»: Ingen slik fil eller filkatalog
rm: klarte ikke å fjerne «/home/kris/.asound*»: Ingen slik fil eller filkatalog
rm: klarte ikke å fjerne «/home/kris/.pulse-cookie»: Ingen slik fil eller filkatalog
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty InRelease
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates InRelease                      
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports InRelease                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty Release.gpg      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease                       
Hent:1 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates Release.gpg [933 B]         
Funnet [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                             
Funnet [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg          
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports Release.gpg
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty Release          
Hent:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]          
Funnet [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                 
Funnet [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                 
Hent:3 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates Release [59,7 kB]           
Hent:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [59,7 kB]         
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports Release                   
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Sources                        
Funnet [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                            
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Sources                  
Funnet [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                      
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Sources                    
Funnet [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                      
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Sources                  
Funnet [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                     
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main i386 Packages                  
Hent:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [44,4 kB]
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted i386 Packages      
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe i386 Packages        
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse i386 Packages      
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-nb                 
Hent:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [700 B]   
Hent:7 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [10,8 kB]   
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-en                 
Hent:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [14 B]
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-nb           
Hent:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [134 kB]
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-en     
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-nb     
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-en           
Hent:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [14 B]
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-nb             
Hent:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [47,2 kB]
Hent:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [1 398 B]
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-en             
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hent:13 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main Sources [119 kB]
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Hent:14 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse Sources [3 527 B]
Funnet [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en      
Hent:15 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe Sources [84,0 kB]
Hent:16 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted Sources [1 408 B]
Hent:17 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main i386 Packages [314 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-nb_NO                    
Hent:18 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted i386 Packages [5 820 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-nb                     
Hent:19 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe i386 Packages [202 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-no_NO                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-no                   
Hent:20 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse i386 Packages [9 545 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-nn_NO                  
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/main Translation-en         
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/multiverse Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/restricted Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-updates/universe Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse Sources
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main i386 Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted i386 Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe i386 Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse i386 Packages
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/main Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/multiverse Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/restricted Translation-en
Funnet [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty-backports/universe Translation-en
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-nb_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-no_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-no
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/main Translation-nn_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-nb_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-no_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-no
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/multiverse Translation-nn_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-nb_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-no_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-no
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/restricted Translation-nn_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-nb_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-no_NO
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-no
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) trusty/universe Translation-nn_NO
Hentet 1 100 kB på 4s (226 kB/s)
Leser pakkelister ... Ferdig
Leser pakkelister ... Ferdig
Skaper oversikt over avhengighetsforhold       
Leser tilstandsinformasjon ... Ferdig   
aptitude er allerede nyeste versjon.
Følgende pakker ble automatisk installert og er ikke lenger påkrevet:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
0 oppgraderte, 0 nylig installerte, 0 å fjerne og 5 ikke oppgradert.
Ingen kandidatversjon funnet for libsdl1.2debian-pulseaudio
Ingen kandidatversjon funnet for libsdl1.2debian-pulseaudio
Disse NYE pakkene vil bli installert:
  gnome-alsamixer hwdata{a} libbonoboui2-0{a} libbonoboui2-common{a} 
  libgail18{a} libgconfmm-2.6-1c2{a} libglade2-0{a} libglademm-2.4-1c2a{a} 
  libgnome-desktop-2-17{a} libgnomecanvas2-0{a} libgnomecanvas2-common{a} 
  libgnomeui-0{a} libgnomeui-common{a} padevchooser paman paprefs{a} 
  pavumeter{a} pulseaudio-module-gconf{a} pulseaudio-module-zeroconf{a} 
0 pakker oppgradert, 19 nylig installert, 0 skal fjernes og 5 skal ikke oppgraderes.
Trenger å hente 975 kB i installasjonspakker. Etter utpakking vil 5 497 kB bli brukt.
Vil du fortsette? [Y/n/?] y
Hent: 1 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libglade2-0 i386 1:2.6.4-2 [43,7 kB]
Hent: 2 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty-updates/main libgail18 i386 2.24.23-0ubuntu1.1 [13,9 kB]
Hent: 3 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libgnomecanvas2-common all 2.30.3-2 [9 080 B]
Hent: 4 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libgnomecanvas2-0 i386 2.30.3-2 [80,9 kB]
Hent: 5 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libbonoboui2-common all 2.24.5-0ubuntu3 [11,4 kB]
Hent: 6 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libbonoboui2-0 i386 2.24.5-0ubuntu3 [149 kB]
Hent: 7 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libgnomeui-common all 2.24.5-3 [16,5 kB]
Hent: 8 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main libgnomeui-0 i386 2.24.5-3 [197 kB]
Hent: 9 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe gnome-alsamixer i386 0.9.7~cvs.20060916.ds.1-5 [51,4 kB]
Hent: 10 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main hwdata all 0.249-1 [26,1 kB]
Hent: 11 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe libgconfmm-2.6-1c2 i386 2.28.3-0ubuntu2 [24,3 kB]
Hent: 12 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe libglademm-2.4-1c2a i386 2.6.7-2ubuntu1 [17,7 kB]
Hent: 13 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe libgnome-desktop-2-17 i386 1:2.32.1-2ubuntu1 [98,8 kB]
Hent: 14 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe padevchooser i386 0.9.4-1.1 [23,0 kB]
Hent: 15 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe paman i386 0.9.4-1ubuntu3 [91,7 kB]
Hent: 16 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main pulseaudio-module-gconf i386 1:4.0-0ubuntu11 [12,1 kB]
Hent: 17 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/main pulseaudio-module-zeroconf i386 1:4.0-0ubuntu11 [18,2 kB]
Hent: 18 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe paprefs i386 0.9.10-1 [61,9 kB]
Hent: 19 [http://no.archive.ubuntu.com/ubuntu/](http://no.archive.ubuntu.com/ubuntu/) trusty/universe pavumeter i386 0.9.3-4 [28,4 kB]
Henta 975 kB på 1s (619 kB/s)        
 Velger den tidligere bortvalgte pakka «libglade2-0:i386».
(Leser database ... 273930 filer og kataloger er for øyeblikket installerte.)
Preparing to unpack .../libglade2-0_1%3a2.6.4-2_i386.deb ...
Unpacking libglade2-0:i386 (1:2.6.4-2) ...
Velger den tidligere bortvalgte pakka «libgail18:i386».
Preparing to unpack .../libgail18_2.24.23-0ubuntu1.1_i386.deb ...
Unpacking libgail18:i386 (2.24.23-0ubuntu1.1) ...
Velger den tidligere bortvalgte pakka «libgnomecanvas2-common».
Preparing to unpack .../libgnomecanvas2-common_2.30.3-2_all.deb ...
Unpacking libgnomecanvas2-common (2.30.3-2) ...
Velger den tidligere bortvalgte pakka «libgnomecanvas2-0:i386».
Preparing to unpack .../libgnomecanvas2-0_2.30.3-2_i386.deb ...
Unpacking libgnomecanvas2-0:i386 (2.30.3-2) ...
Velger den tidligere bortvalgte pakka «libbonoboui2-common».
Preparing to unpack .../libbonoboui2-common_2.24.5-0ubuntu3_all.deb ...
Unpacking libbonoboui2-common (2.24.5-0ubuntu3) ...
Velger den tidligere bortvalgte pakka «libbonoboui2-0:i386».
Preparing to unpack .../libbonoboui2-0_2.24.5-0ubuntu3_i386.deb ...
Unpacking libbonoboui2-0:i386 (2.24.5-0ubuntu3) ...
Velger den tidligere bortvalgte pakka «libgnomeui-common».
Preparing to unpack .../libgnomeui-common_2.24.5-3_all.deb ...
Unpacking libgnomeui-common (2.24.5-3) ...
Velger den tidligere bortvalgte pakka «libgnomeui-0:i386».
Preparing to unpack .../libgnomeui-0_2.24.5-3_i386.deb ...
Unpacking libgnomeui-0:i386 (2.24.5-3) ...
Velger den tidligere bortvalgte pakka «gnome-alsamixer».
Preparing to unpack .../gnome-alsamixer_0.9.7~cvs.20060916.ds.1-5_i386.deb ...
Unpacking gnome-alsamixer (0.9.7~cvs.20060916.ds.1-5) ...
Velger den tidligere bortvalgte pakka «hwdata».
Preparing to unpack .../hwdata_0.249-1_all.deb ...
Unpacking hwdata (0.249-1) ...
Velger den tidligere bortvalgte pakka «libgconfmm-2.6-1c2».
Preparing to unpack .../libgconfmm-2.6-1c2_2.28.3-0ubuntu2_i386.deb ...
Unpacking libgconfmm-2.6-1c2 (2.28.3-0ubuntu2) ...
Velger den tidligere bortvalgte pakka «libglademm-2.4-1c2a».
Preparing to unpack .../libglademm-2.4-1c2a_2.6.7-2ubuntu1_i386.deb ...
Unpacking libglademm-2.4-1c2a (2.6.7-2ubuntu1) ...
Velger den tidligere bortvalgte pakka «libgnome-desktop-2-17».
Preparing to unpack .../libgnome-desktop-2-17_1%3a2.32.1-2ubuntu1_i386.deb ...
Unpacking libgnome-desktop-2-17 (1:2.32.1-2ubuntu1) ...
Velger den tidligere bortvalgte pakka «padevchooser».
Preparing to unpack .../padevchooser_0.9.4-1.1_i386.deb ...
Unpacking padevchooser (0.9.4-1.1) ...
Velger den tidligere bortvalgte pakka «paman».
Preparing to unpack .../paman_0.9.4-1ubuntu3_i386.deb ...
Unpacking paman (0.9.4-1ubuntu3) ...
Velger den tidligere bortvalgte pakka «pulseaudio-module-gconf».
Preparing to unpack .../pulseaudio-module-gconf_1%3a4.0-0ubuntu11_i386.deb ...
Unpacking pulseaudio-module-gconf (1:4.0-0ubuntu11) ...
Velger den tidligere bortvalgte pakka «pulseaudio-module-zeroconf».
Preparing to unpack .../pulseaudio-module-zeroconf_1%3a4.0-0ubuntu11_i386.deb ...
Unpacking pulseaudio-module-zeroconf (1:4.0-0ubuntu11) ...
Velger den tidligere bortvalgte pakka «paprefs».
Preparing to unpack .../paprefs_0.9.10-1_i386.deb ...
Unpacking paprefs (0.9.10-1) ...
Velger den tidligere bortvalgte pakka «pavumeter».
Preparing to unpack .../pavumeter_0.9.3-4_i386.deb ...
Unpacking pavumeter (0.9.3-4) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setter opp libglade2-0:i386 (1:2.6.4-2) ...
Setter opp libgail18:i386 (2.24.23-0ubuntu1.1) ...
Setter opp libgnomecanvas2-common (2.30.3-2) ...
Setter opp libgnomecanvas2-0:i386 (2.30.3-2) ...
Setter opp libbonoboui2-common (2.24.5-0ubuntu3) ...
Setter opp libbonoboui2-0:i386 (2.24.5-0ubuntu3) ...
Setter opp libgnomeui-common (2.24.5-3) ...
Setter opp libgnomeui-0:i386 (2.24.5-3) ...
Setter opp gnome-alsamixer (0.9.7~cvs.20060916.ds.1-5) ...
Setter opp hwdata (0.249-1) ...
Setter opp libgconfmm-2.6-1c2 (2.28.3-0ubuntu2) ...
Setter opp libglademm-2.4-1c2a (2.6.7-2ubuntu1) ...
Setter opp libgnome-desktop-2-17 (1:2.32.1-2ubuntu1) ...
Setter opp padevchooser (0.9.4-1.1) ...
Setter opp paman (0.9.4-1ubuntu3) ...
Setter opp pulseaudio-module-gconf (1:4.0-0ubuntu11) ...
Setter opp pulseaudio-module-zeroconf (1:4.0-0ubuntu11) ...
Setter opp paprefs (0.9.10-1) ...
Setter opp pavumeter (0.9.3-4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
                                               
H/W path        Device      Class          Description
======================================================
                            system         Vostro 3300 (To be filled by O.E.M.)
/0                          bus            030DMJ
/0/4                        processor      Intel(R) Celeron(R) CPU        P4500 
/0/4/5                      memory         32KiB L1 cache
/0/4/6                      memory         256KiB L2 cache
/0/4/7                      memory         2MiB L3 cache
/0/4/0.1                    processor      Logical CPU
/0/4/0.2                    processor      Logical CPU
/0/4/0.3                    processor      Logical CPU
/0/4/0.4                    processor      Logical CPU
/0/4/0.5                    processor      Logical CPU
/0/4/0.6                    processor      Logical CPU
/0/4/0.7                    processor      Logical CPU
/0/4/0.8                    processor      Logical CPU
/0/4/0.9                    processor      Logical CPU
/0/4/0.a                    processor      Logical CPU
/0/4/0.b                    processor      Logical CPU
/0/4/0.c                    processor      Logical CPU
/0/4/0.d                    processor      Logical CPU
/0/4/0.e                    processor      Logical CPU
/0/4/0.f                    processor      Logical CPU
/0/4/0.10                   processor      Logical CPU
/0/1d                       memory         2GiB System Memory
/0/1d/0                     memory         DIMM [empty]
/0/1d/1                     memory         DIMM [empty]
/0/1d/2                     memory         2GiB DIMM DDR3 Synchronous 1333 MHz (
/0/1d/3                     memory         DIMM [empty]
/0/0                        memory         64KiB BIOS
/0/1                        processor      
/0/1/0.1                    processor      Logical CPU
/0/1/0.2                    processor      Logical CPU
/0/1/0.3                    processor      Logical CPU
/0/1/0.4                    processor      Logical CPU
/0/1/0.5                    processor      Logical CPU
/0/1/0.6                    processor      Logical CPU
/0/1/0.7                    processor      Logical CPU
/0/1/0.8                    processor      Logical CPU
/0/1/0.9                    processor      Logical CPU
/0/1/0.a                    processor      Logical CPU
/0/1/0.b                    processor      Logical CPU
/0/1/0.c                    processor      Logical CPU
/0/1/0.d                    processor      Logical CPU
/0/1/0.e                    processor      Logical CPU
/0/1/0.f                    processor      Logical CPU
/0/1/0.10                   processor      Logical CPU
/0/100                      bridge         Core Processor DRAM Controller
/0/100/2                    display        Core Processor Integrated Graphics Co
/0/100/16                   communication  5 Series/3400 Series Chipset HECI Con
/0/100/1a                   bus            5 Series/3400 Series Chipset USB2 Enh
/0/100/1b                   multimedia     5 Series/3400 Series Chipset High Def
/0/100/1c                   bridge         5 Series/3400 Series Chipset PCI Expr
/0/100/1c.1                 bridge         5 Series/3400 Series Chipset PCI Expr
/0/100/1c.1/0   wlan0       network        BCM43224 802.11a/b/g/n
/0/100/1c.2                 bridge         5 Series/3400 Series Chipset PCI Expr
/0/100/1c.2/0   eth0        network        RTL8111/8168/8411 PCI Express Gigabit
/0/100/1c.4                 bridge         5 Series/3400 Series Chipset PCI Expr
/0/100/1d                   bus            5 Series/3400 Series Chipset USB2 Enh
/0/100/1e                   bridge         82801 Mobile PCI Bridge
/0/100/1f                   bridge         Mobile 5 Series Chipset LPC Interface
/0/100/1f.2                 storage        5 Series/3400 Series Chipset 6 port S
/0/100/1f.3                 bus            5 Series/3400 Series Chipset SMBus Co
/0/100/1f.6                 generic        5 Series/3400 Series Chipset Thermal 
/0/101                      bridge         Core Processor QuickPath Architecture
/0/102                      bridge         Core Processor QuickPath Architecture
/0/103                      bridge         Core Processor QPI Link 0
/0/104                      bridge         Core Processor QPI Physical 0
/0/105                      bridge         Core Processor Reserved
/0/106                      bridge         Core Processor Reserved
/0/2            scsi0       storage        
/0/2/0.0.0      /dev/sda    disk           320GB WDC WD3200BEKT-7
/0/2/0.0.0/1    /dev/sda1   volume         243MiB Linux filesystem partition
/0/2/0.0.0/2    /dev/sda2   volume         297GiB Extended partition
/0/2/0.0.0/2/5  /dev/sda5   volume         297GiB Linux LVM Physical Volume part
/0/3            scsi1       storage        
/0/3/0.0.0      /dev/cdrom  disk           DVD+-RW GU40N
/1                          power          DELL 7W5X004
totalt 0
crw-rw----+  1 root audio 116, 33 sep.  15 18:54 timer
crw-rw----+  1 root audio 116,  1 sep.  15 18:54 seq
crw-rw----+  1 root audio 116,  4 sep.  15 18:54 hwC0D0
crw-rw----+  1 root audio 116,  5 sep.  15 18:54 controlC0
drwxr-xr-x   2 root root       60 sep.  15 18:54 by-path
drwxr-xr-x   3 root root      180 sep.  15 18:54 .
crw-rw----+  1 root audio 116,  2 sep.  15 18:55 pcmC0D0p
crw-rw----+  1 root audio 116,  3 sep.  15 18:55 pcmC0D0c
drwxr-xr-x  17 root root     4200 sep.  15 18:59 ..
cat: /dev/sndstat: Ingen slik fil eller filkatalog
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 12)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 12)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.2 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 [8086:3b46] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b0b] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 06)
12:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
13:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
ff:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
ff:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6421 Microdia 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
/usr/sbin/alsactl
Specified filename /dev/dsp does not exist.
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  kris       2008 F.... pulseaudio
dpkg-query: no path found matching pattern *bin/slmodemd*
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000] found SMP MP-table at [mem 0x000fcda0-0x000fcdaf] mapped at [c00fcda0]
[    0.216124] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.231250] ACPI: No dock devices found.
[    0.268662] Found 1 acpi root devices
[    0.279612] pci_bus 0000:ff: No busn resource found for root bus, will use [bus ff-ff]
[    0.291237] pnp: PnP ACPI: found 11 devices
[    1.017068] audit: initializing netlink socket (disabled)
[    1.017081] type=2000 audit(1410800038.892:1): initialized
[    1.403024] libphy: Fixed MDIO Bus: probed
[    1.422537] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.422675] hub 1-0:1.0: USB hub found
[    1.438518] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.438654] hub 2-0:1.0: USB hub found
[    1.485905] IMA: No TPM chip found, activating TPM-bypass!
[    1.487057] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.699815] isapnp: No Plug & Play device found
[    1.898821] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.899243] hub 1-1:1.0: USB hub found
[    2.142990] usb 2-1: New USB device found, idVendor=8087, idProduct=0020
[    2.143631] hub 2-1:1.0: USB hub found
[    2.384645] usb 1-1.4: New USB device found, idVendor=0c45, idProduct=6421
[   22.962978] lp: driver loaded but no devices found
[   23.182438] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   23.201605] intel ips 0000:00:1f.6: No CPUID match found.
[   23.466624] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   23.479705] type=1400 audit(1410800061.487:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=410 comm="apparmor_parser"
[   23.479715] type=1400 audit(1410800061.487:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[   23.479721] type=1400 audit(1410800061.487:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   23.480876] type=1400 audit(1410800061.491:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=410 comm="apparmor_parser"
[   23.480885] type=1400 audit(1410800061.491:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   23.481254] type=1400 audit(1410800061.491:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=410 comm="apparmor_parser"
[   23.893940] snd_hda_codec: module has bad taint, not creating trace events
[   23.896427] snd_hda_controller: module has bad taint, not creating trace events
[   23.898666] snd_hda_intel 0000:00:1b.0: Probing card using HDA DKMS, version 0.201409101516~ubuntu14.04.1
[   23.898899] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   23.926247] sound hdaudioC0D0: autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   23.926254] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.926256] sound hdaudioC0D0:    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   23.926258] sound hdaudioC0D0:    mono: mono_out=0x0
[   23.926260] sound hdaudioC0D0:    inputs:
[   23.926263] sound hdaudioC0D0:      Internal Mic=0x11
[   23.926266] sound hdaudioC0D0:      Mic=0xa
[   23.955071] input: HDA Intel MID Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   23.956675] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.063119] uvcvideo: Found UVC 1.00 device Laptop_Integrated_Webcam_2M (0c45:6421)
[   25.735112] type=1400 audit(1410800063.743:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=727 comm="apparmor_parser"
[   25.735123] type=1400 audit(1410800063.743:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=727 comm="apparmor_parser"
[   25.735777] type=1400 audit(1410800063.743:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=727 comm="apparmor_parser"
[   26.680923] type=1400 audit(1410800064.691:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=848 comm="apparmor_parser"
[   55.865744] audit_printk_skb: 105 callbacks suppressed
[   55.865749] type=1400 audit(1410800093.871:47): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1690 comm="apparmor_parser"
[   55.865758] type=1400 audit(1410800093.871:48): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1690 comm="apparmor_parser"
[   55.866409] type=1400 audit(1410800093.871:49): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1690 comm="apparmor_parser"
sudo: /etc/init.d/sl-modem-daemon: command not found
    Manufacturer: Intel            
    Serial Number: To Be Filled By O.E.M.
    Manufacturer: SMP-SDI2.8         
    Manufacture Date: 10/31/2006
    Serial Number: 887      
    Release Date: 05/21/2010
        Serial services are supported (int 14h)
    Manufacturer: Dell Inc.
    Product Name: 030DMJ
    Serial Number: .G1C97N1.CN7016609B000R.           
    Manufacturer: Dell Inc.
    Serial Number: G1C97N1
    Manufacturer: Dell Inc.
    Product Name: Vostro 3300
    Serial Number: G1C97N1
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Manufacturer: Not Specified
    Serial Number: Not Specified
    Manufacturer: Undefined       
    Serial Number: 62EEA6EB  
    Manufacturer: Not Specified
    Serial Number: Not Specified
snd_seq_dummy          12686  0 
snd_hda_codec_idt      53583  1 
snd_hda_codec_generic    62873  1 snd_hda_codec_idt
snd_hda_intel          29473  2 
snd_hda_controller     30673  1 snd_hda_intel
snd_hda_codec         120268  4 snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  3 snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_page_alloc         14230  3 snd_pcm,snd_hda_intel,snd_hda_controller
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  3 snd_seq_midi_event,snd_seq_dummy,snd_seq_midi
snd_seq_device         14137  4 snd_seq,snd_rawmidi,snd_seq_dummy,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60939  16 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_dummy,snd_seq_midi
soundcore              12600  2 snd,snd_hda_codec
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    base volume: 100%
                 0,00 dB
    volume steps: 65537
    muted: no
    current latency: 0,00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0,00 ms; range is 0,50 .. 371,52 ms
    card: 0 <alsa_card.pci-0000_00_1b.0>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "92HD81B1X5 Analog"
        alsa.id = "92HD81B1X5 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel MID"
        alsa.long_card_name = "HDA Intel MID at 0xfbc00000 irq 48"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "3b56"
        device.product.name = "5 Series/3400 Series Chipset High Definition Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog stereokanal"
        device.description = "Innebygd lydenhet Analog stereokanal"
        alsa.mixer_name = "IDT 92HD81B1X5"
        alsa.components = "HDA:111d7605,1028043f,00100104"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output-speaker: Høyttalere (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Hodetelefoner (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output-speaker>
>>> **** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: 92HD81B1X5 Analog [92HD81B1X5 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Unloading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-idt snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer (failed: modules still loaded: snd-hda-codec-idt snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-timer).
Loading ALSA sound driver modules: snd-seq-dummy snd-hda-codec-idt snd-hda-codec-generic snd-hda-intel snd-hda-controller snd-hda-codec snd-hwdep snd-pcm snd-page-alloc snd-seq-midi snd-seq-midi-event snd-rawmidi snd-seq snd-seq-device snd-timer.
Oppsummering av programstøtte for 'OKOK1':

Du har 1397 pakker (81.9%) som støttes frem til mai 2019 (5y)
Du har 207 pakker (12.1%) som støttes frem til mai 2017 (3y)
Du har 47 pakker (2.8%) som støttes frem til februar 2015 (9m)
Du har 16 pakker (0.9%) som støttes frem til juni 2015 (9m)

Du har 1 pakker (0.1%) som ikke lenger kan lastes ned
Du har 37 pakker (2.2%) som ikke støttes

Kjør med --show-unsupported, --show-supported eller --show-all for flere detaljer
  *-multimedia            
       description: Audio device
       product: 5 Series/3400 Series Chipset High Definition Audio
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:48 memory:fbc00000-fbc03fff



---

