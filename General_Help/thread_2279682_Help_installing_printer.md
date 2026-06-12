---
title: "Help installing printer"
date: 2015-05-25
forum: General Help
---

### Post by cracktor on 2015-05-25
Hello,

I tried installing my printer, but i fail misarable.. 

samsung xpress m2022 
First i tried downloading the driver and following this guide [http://askubuntu.com/questions/170880/how-do-i-install-the-drivers-for-my-samsung-printer]("http://guide")
> cd ULD_v1.00.35.tar.gz
bash: cd: ULD_v1.00.35.tar.gz: No such file or directory

So i moved the driver to the desktop, extracted and tried this:

> *****:~/Desktop$ cd uld*****:~/Desktop/uld$ sudo install.sh
[sudo] password for ***: 
sudo: install.sh: command not found
*****:~/Desktop/uld$




So i tried installing is by system/settings printer, and i got this error > dle - File "/usr/lib/cups/filter/rastertospl" not available: No such file or directory

i found this file in the printer driver which i downloaded and extracted. But when i tried to move it to the right folder it says ' acces denied' .

Any help appriciated!

---

### Post by mastablasta on 2015-05-25
have you tried this method: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

---

### Post by cracktor on 2015-05-25
> **mastablasta said:**
> have you tried this method: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)

i don' t get this either.. I dont think the problem is with my machine, i just dont know how to install anything!

---

### Post by QDR06VV9 on 2015-05-25
I would just set up the Repository.
> **Setting Up the Repository**

 
[LIST=1]
[*]If you performed any installations of the Unified Linux Driver  performed using the Samsung installer, these must be completely removed  before using the .debs in this repository.  See the [uninstallation information]("http://www.bchemnet.com/suldr/suld.html") for your version of the driver. 
[*]Do one of the following to enable the repository (all are equivalent).
[LIST]
[*]Using the terminal:
[LIST]
[*]To /etc/apt/sources.list (root/sudo access required to edit), add the line:
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra 
[*]Enter the following in a terminal (as root):
bash -c 'echo "deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra" >> /etc/apt/sources.list'
Or if using sudo:
sudo bash -c 'echo "deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra" >> /etc/apt/sources.list' 
[/LIST]
  
[*]Or using a graphical package manager (Synaptic, Ubuntu Software Center, etc.):
[LIST]
[*]Edit the repository settings (e.g., Synpatic go to Settings -> Repositories) to add:
deb [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/) debian extra 
[*]Or if multi-line input is required:
URI: [http://www.bchemnet.com/suldr/](http://www.bchemnet.com/suldr/)
Distribution: debian
Section: extra
[*]Install the GPG key (last update: 18 Oct 2009) for the repository  (if you skip this step, you will get warnings about installing  unauthenticated packages), using one of the following methods.
[LIST]
[*]In a terminal, as root, enter the command (the - marks are important):
wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | apt-key add -
Or if you are using sudo:
sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
[*]Download [the key file]("http://www.bchemnet.com/suldr/suldr.gpg") and add it to your graphical package manager list of keys.
[*]Download [the key file]("http://www.bchemnet.com/suldr/suldr.gpg") and execute the following (as root) in a terminal, in the folder with the key file:
apt-key add suldr.gpg
Or if you are using sudo:
sudo apt-key add suldr.gpg
[/LIST]

[*]Refresh your repository listings:
[LIST]
[*]On a terminal (as root):
apt-get update
Or if using sudo:
sudo apt-get update
[/LIST]
 
[/LIST]
  
[/LIST]
  
[/LIST]

Pretty straight forward.;)
Regards

---

### Post by cracktor on 2015-05-25
> **runrickus said:**
> I would just set up the Repository.

Pretty straight forward.;)
Regards


Well i did this, and i think it succeded. But still cant print!
the problem is that i have no idea what i' m doing..

> GPG error: [http://www.bchemnet.com](http://www.bchemnet.com) debian InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C95104E509BAC46D


---

### Post by QDR06VV9 on 2015-05-25
> **cracktor said:**
> Well i did this, and i think it succeded. But still cant print!
the problem is that i have no idea what i' m doing..
Try this with the problem on key
```
sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
```
Update and install the driver I think you were wanting v1.00.35. But I don't know for sure That was in your first post.
Regards

---

### Post by cracktor on 2015-05-25
> **runrickus said:**
> Try this with the problem on key
```
sudo wget -O - [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg) | sudo apt-key add -
```
Update and install the driver I think you were wanting v1.00.35. But I don't know for sure That was in your first post.
Regards


> --2015-05-25 20:15:30--  [http://www.bchemnet.com/suldr/suldr.gpg](http://www.bchemnet.com/suldr/suldr.gpg)
Resolving [www.bchemnet.com](www.bchemnet.com) ([www.bchemnet.com](www.bchemnet.com))... 173.236.28.2
Connecting to [www.bchemnet.com](www.bchemnet.com) ([www.bchemnet.com)|173.236.28.2|:80](www.bchemnet.com)|173.236.28.2|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1690 (1.7K)
Saving to: ‘STDOUT’


100%[======================================>] 1,690       --.-K/s   in 0s      


2015-05-25 20:15:30 (106 MB/s) - written to stdout [1690/1690]




Is this good? :P

---

### Post by QDR06VV9 on 2015-05-25
> **cracktor said:**
> Is this good? :P
Yes.
Now just update packages 
```
sudo apt-get update
```

And install the driver ***for your printer***.
Probably Synaptic would be better so you can see what driver is being shown.
> Regardless of the particular package installed, you will then need to  set up the printer using any printer management tool (the default one in  your distribution, the CUPS web interface, or the Samsung  Configurator).
I'll stick around for a little while to see how your doing.
Regards:p
If you are successful Please Mark the thread as Solved so others may gain from it.

---

### Post by cracktor on 2015-05-25
I solved it!

Asked thesame question under the dutch forums and did this:

Source:

[https://sites.google.com/site/computertip/samsungprinters](https://sites.google.com/site/computertip/samsungprinters)

> [I]**Let op:** krijgt u nu een melding dat het bestand of de map niet bestaat? Dan hebt u de oude versie van het stuurprogramma binnengehaald, voor oudere apparaten. Want het nieuwe stuurprogramma is er alleen voor nieuwere printers. Kopieer en plak dan de volgende toverspreuk in de terminal:
[COLOR=#0000FF]cd Downloads && tar xvzf ~/Downloads/*UnifiedLinuxDriver*.tar.gz[/COLOR]


4. Kopieer en plak vervolgens in het terminalvenster:
[COLOR=#0000FF]cd ~/Downloads/uld[/COLOR]

Druk op Enter.

[I]**Let op:** bij de oude versie van het stuurprogramma krijgt u nu wederom een melding dat het bestand of de map niet bestaat. Kopieer en plak in dat geval de volgende toverspreuk in de terminal:
[COLOR=#0000FF]cd ~/Downloads/cdroot/Linux[/COLOR]

Druk op Enter.


5. Vervolgens in de terminal (kopieer en plak): 
[COLOR=#0000FF]sudo sh install.sh[/COLOR]

druk op Enter. 

Tik desgevraagd uw wachtwoord in. Uw wachtwoord blijft geheel onzichtbaar, u ziet zelfs geen sterretjes, dat hoort zo.
Druk wederom op Enter.[/I][/I]

The main problem was (as far as i know) that i got the old version of the driver. Thats why i got the error code.

Thx for all the help. i can print now :)

---

### Post by QDR06VV9 on 2015-05-25
Great Good Work=d> But that posted in the Quote in my post.
> If you performed any installations of the Unified Linux Driver   performed using the Samsung installer, these must be completely removed   before using the .debs in this repository.  See the [uninstallation information]("http://www.bchemnet.com/suldr/suld.html") for your version of the driver.
Success is always a good thing no matter how.
Kind Regards

---

### Post by mastablasta on 2015-05-26
I hope the driver "sticks" after updates. otherwise you keep have to repeat the process. plus it wont' upgrade automatically they way you installed it. if you added the repository - driver would then appear in software center and then you can install it and get's automatically updates along with other updates.

with manual install you need to uninstall the old and then install the new version.

---

### Post by QDR06VV9 on 2015-05-26
> **mastablasta said:**
> I hope the driver "sticks" after updates. otherwise you keep have to repeat the process. plus it wont' upgrade automatically they way you installed it. if you added the repository - driver would then appear in software center and then you can install it and get's automatically updates along with other updates.

with manual install you need to uninstall the old and then install the new version.
+1;) Could not agree more!

---

### Post by $yl9pAR%t on 2015-05-26
1. Back to your opening post, you forgot "sh", you should type in terminal:

```
sudo sh install.sh
```

2. There is something wrong with your link to askubuntu guide. I cannot open this site.

---

### Post by Taffywiking on 2015-12-11
Thanks Cracktor, you cleared my logjam!  All that complicated stuff was doing my head in, but your straightforward advice in Dutch (a language that I don't speak) did the trick "sudo sh install.sh"

---

### Post by Teocci on 2016-03-17
Just to sum up: 
1. download the [samsung drivers here]("http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=UNI_HK_EN&CttFileID=5768673&CDCttType=DR&ModelType=N&ModelName=ML-3310ND&VPath=DR/201407/20140710110338169/ULD_V1.00.27.04.tar.gz").
2. After that using the terminal uncompress the file with the following code:
> cd Downloads && tar xvzf ~/Downloads/ULD_V1.00.27.04.tar.gz
3. Move to the uld directory
> cd ~/Downloads/uld
4. Finally, execute the installer:
> sudo ./install.sh
5. The go to System Settings -> Printers -> Add->Network->Select your Printer, Select your model. and done.

Enjoy your printer installed.

---

### Post by oldos2er on 2016-03-17
Old thread closed.

---

