---
title: "Compie xmms"
date: 2005-06-12
forum: General Help
---

### Post by wytzehoekstra on 2005-06-12
Hello can any one tell my how to compile a certain software like fi: xmms/octave

Steps:
1. "/configure"  in the folder where the source is saved?
2.if approved  "make" in the folder where the source is saved?
3.if approved  "make install" in the folder where the source is save 
   Where will it be installe?

Oke hope anyone can tell me if this is right. Thanks!

---

### Post by word_virus on 2005-06-12
[QUOTE=wytzehoekstra]Hello can any one tell my how to compile a certain software like fi: xmms/octave

Steps:
1. "/configure"  in the folder where the source is saved?
2.if approved  "make" in the folder where the source is saved?
3.if approved  "make install" in the folder where the source is save 
   Where will it be installe?

Oke hope anyone can tell me if this is right. Thanks![/QUOTE]

1. Yes.  If you want to see the special options you can pass to configure, type "./configure --help" first. If you want to specify the directory to install the program in type "./configure --prefix=/directory/name/here"

2. Yes

3. "sudo make install" instead of "make install".  This will prompt you for your password, as well.  The output of this command will show you where the program was installed.

---

### Post by wytzehoekstra on 2005-06-12
oke so to summarize 3 possibilities it would go like this?:

1. a. Download xmms_fullversion??? [-X .deb from:
        [http://packages.debian.org/unstable/sound/xmms.html](http://packages.debian.org/unstable/sound/xmms.html)
        Will i need to install the related packages?
        Or are they already installed in a standard Ubuntu 5.04 
        setup or included in the xmms_fullversion???. [-X deb
        Can I check this using the "/configure" cmd without harming my computer. 
    b. sudo dpkg -i xmms_fullversion???. [-X deb
    c. I am ready and won't need to install any further plugins/libraries/packages
2. a. Connect to the internet and follow the steps at:
         [http://ubuntuguide.org/](http://ubuntuguide.org/)
    b. This means first adapt the reposteries.I supose Synaptic will look at the given     
         reposteries and download and install the packages needed for the 
         codecs(=plugins? [-X ). 
        [B] What happens if you run: "gst-register-0.8" on a computer that isn't 
         connected to the internet?[/B]
         I**s this a bypass command so you wouldn't need to register?** ](*,) 
     c. Then run "sudo apt-get install xmms" 
         what will be downloaded and installed. A .deb package?
     d. With 
         "wget -c http://frankandjacq.com/ubuntuguide/xmms-wma_1.0.4-2_i386.deb"
          i swill download what?. If I look in this .deb file it is a lot smaller than the     
          "fullversion".
     e. final step would be "sudo dpkg -i xmms-wma_1.0.4-2_i386.deb".
3. a. i need to get the source code of xmms
    b. install the needed libraries/plugins/packages/
    c. follow the steps in the first reply of this subject.


Oke hope it doesn't sound like Im already becoming a cyborg or something. Thanks alot for any help.

---

### Post by angkor on 2005-06-12
Maybe I'm missing something here but what's wrong with just: sudo apt-get install xmms and installing the necessary plugins after that?

---

### Post by wytzehoekstra on 2005-06-12
well the problem first of all is that I would like to know what i am doing and understand and beside this my neighbour doens't have internet.

---

### Post by angkor on 2005-06-12
No internet :shock: 

Aah I understand...Well if _you_ do have an inet connection you could see what xmms' dependencies are with:

sudo apt-cache depends xmms

Then you will need to download all needed packages and burn em and install em all on your neighbours comp with dpkg -i [package-name]. It might be necessary to install em in a specific order.

---

### Post by wytzehoekstra on 2005-06-12
just wanted to ask if there is a quicker way.. ](*,) 
Maybe i should persue him to buy a network card...

One more question how will I know if a soundcard is installed in a computer or not.. :razz:  :^o  should have asked this question first :roll: but at least i got a better picture how debian/ubuntu works...Thanks for your reply.

---

### Post by angkor on 2005-06-13
the command lspci should give you information about the soundcard

---

