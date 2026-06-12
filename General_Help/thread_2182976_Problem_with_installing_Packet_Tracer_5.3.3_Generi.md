---
title: "Problem with installing Packet Tracer 5.3.3 Generic Fedora.bin on ubunut 13.04 x64"
date: 2013-10-23
forum: General Help
---

### Post by zsxTFfn on 2013-10-23
Hello

I am completely new to ubuntu, I am a student and is required to install Packet tracer, I am installing Packet Tracer 5.3.3 Generic Fedora.bin on ubuntu 13.04 x64. I downloaded the linux version of the PT and I started typing the following commands in the terminal:
"chmod +x PacketTracer533_Generic_Fedora.tar.gz" (Press enter) > "sudo ./PacketTracer533_Generic_Fedora.tar.gz" > (then it asks me for password which I type and enter.) > (the following error comes up) - "./PacketTracer533_Generic_Fedora.tar.gz: 1: ./PacketTracer533_Generic_Fedora.tar.gz: Syntax error: ")" unexpected". I have tried putting the [file name] into brackets and quotaitions marks. I believe I am missing a character in the code. 
I have tried extracting it and going through the same method ([file name] = "PacketTracer53" - name of the extracted folder, btw all the files are located in the "Home" folder).
There is also an "Install" txt file with what it seems are intrusctions. They start: 
" 
#!/bin/bash
# Thanks to Felix Wolf (felix@bar.bz) for providing this install script.
initInstall ()
{
echo
echo Welcome to Cisco Packet Tracer 5.3.3 Installation
"
 (nxt theres the please accept terms and conditions etc)
Does anyone know what do I have to do? what do these commands mean? 
Thank you very much

---

### Post by oldos2er on 2013-10-23
Moved to General Help.

You should extract the tar.gz first ```
tar -xzvf PacketTracer533_Generic_Fedora.tar.gz
``` and assuming a *.bin file is extracted you would then run chmod +x on it, then execute it with ./PacketTracer533_Generic_Fedora.bin (if that's the file name). Add 'sudo' only if you're sure you need it.

---

