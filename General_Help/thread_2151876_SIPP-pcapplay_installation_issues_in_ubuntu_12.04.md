---
title: "SIPP-pcapplay installation issues in ubuntu 12.04"
date: 2013-06-06
forum: General Help
---

### Post by shakthi90 on 2013-06-06
[FONT=DejaVu Sans Mono]I downloaded sipp (a sip packet creator), then extracted the files to sipp.svn folder.
When I give "make pcapplay", getting the following error[/FONT]
   
[FONT=FreeMono, monospace]oxovalchn1@oxovalchn1:~/sipp.svn$ make pcapplay
make OSNAME=`uname|sed -e "s/CYGWIN.*/CYGWIN/"` MODELNAME=`uname -m|sed "s/Power Macintosh/ppc/"` OBJ_PCAPPLAY="send_packets.o prepare_pcap.o" PCAPPLAY_LIBS="-lpcap" PCAPPLAY="-DPCAPPLAY" sipp
make[1]: Entering directory `/home/oxovalchn1/sipp.svn'
make[1]: `sipp' is up to date.
make[1]: Leaving directory `/home/oxovalchn1/sipp.svn'

[/FONT][FONT=DejaVu Sans Mono]Can any one help me on resolving the issue?[/FONT][FONT=FreeMono, monospace][/FONT][FONT=DejaVu Sans Mono] The following packages are already installed
[/FONT]   
[FONT=FreeMono, monospace]sudo apt-get install pcaputils
sudo apt-get install libssl-dev libpcap-dev libncurses5-dev[/FONT]

---

### Post by shakthi90 on 2013-06-06
> **shakthi90 said:**
> [FONT=DejaVu Sans Mono]I downloaded sipp (a sip packet creator), then extracted the files to sipp.svn folder.
When I give "make pcapplay", getting the following error[/FONT]
   
[FONT=FreeMono]oxovalchn1@oxovalchn1:~/sipp.svn$ make pcapplay
make OSNAME=`uname|sed -e "s/CYGWIN.*/CYGWIN/"` MODELNAME=`uname -m|sed "s/Power Macintosh/ppc/"` OBJ_PCAPPLAY="send_packets.o prepare_pcap.o" PCAPPLAY_LIBS="-lpcap" PCAPPLAY="-DPCAPPLAY" sipp
make[1]: Entering directory `/home/oxovalchn1/sipp.svn'
make[1]: `sipp' is up to date.
make[1]: Leaving directory `/home/oxovalchn1/sipp.svn'

[/FONT][FONT=DejaVu Sans Mono]Can any one help me on resolving the issue?[/FONT][FONT=DejaVu Sans Mono] The following packages are already installed
[/FONT]   
[FONT=FreeMono]sudo apt-get install pcaputils
sudo apt-get install libssl-dev libpcap-dev libncurses5-dev[/FONT]

After this when I try to run a SIPP scenario, I get the below output.
   
[FONT=FreeMono, monospace]oxovalchn1@oxovalchn1:~/sipp.svn$ sudo ./sipp -sf term.xml 192.168.1.65 -inf term.csv -trace_err -trace_msg -aa -i 192.168.1.65[/FONT] [FONT=FreeMono, monospace]2013-06-06	14:44:58:303	1370510098.303104: The auto_media_port keyword requires PCAPPLAY.[/FONT]

---

### Post by shakthi90 on 2013-06-06
I gave 

~/sipp.svn$make clean
~/sipp.svn$make
~/sipp.svn$make pcapplay

then every thing worked fine

---

