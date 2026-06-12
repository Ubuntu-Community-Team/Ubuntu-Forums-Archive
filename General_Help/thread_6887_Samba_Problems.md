---
title: "Samba Problems"
date: 2004-12-02
forum: General Help
---

### Post by Sniffer on 2004-12-02
Hi fellows, really need your help in this one.

My Server: Warty installed and fully updated, the version of samba it's 3.0.7 stable.

Username: sniffer
Pass:XXXXX


My Client: I have a Windows XP computer where i have the follow:

Username: Admin (yes, with a capital A)
Pass: XXXXX


Then i went to the unofficial ubuntu guide and have done this:

  01) Read General Notes
  02) Read How to add extra repositories?
  03) $ sudo apt-get install samba
  04) $ sudo apt-get install smbfs (yes, the stable versions)


Then this: to configure my workgroup

How to change computer Domain/Workgroup?
  01) Read General Notes
  02) Read How to install Samba Server for file sharing service?
  03) Computer -> System Configuration -> Networking
  04) General Tab -> Windows Networking -> 
      04a) Enable Windows networking (Checked)
      04b) Domain / Workgroup: (Fill in the computer Domain/Workgroup)

then this:

  01) Read General Notes
  02) Read How to install Samba Server for file sharing service?
  03) $ sudo mkdir /home/public
  04) $ sudo chmod 777 /home/public/
  05) $ sudo chmod +t /home/public/
  06) $ sudo gedit /etc/samba/smb.conf
  07) Find this line
      ...
      ;   security = user
      ...
  08) Replace with the following line
         security = share
  09) Append the following lines at the end of file
      [public]
         comment = Public Folder
         path = /home/public
         public = yes
         writable = yes
         create mask = 0777
         directory mask = 0777
         force user = nobody
         force group = nogroup
  10) Save the edited file (sample)
  11) $ sudo testparm
  12) $ sudo /etc/init.d/samba restart

Then i configure firestarter to open ports for smb (137-139), but......didn't work..i'm missing something....


No i didn't have created any username for samba, and i think this way i don't have to??!! I went to my xp computer, i could see my server on the network...but when pressing on it appears i don't have permissions to enter it......

My questions, do i have to create a user for samba??, what it should be?? the same as i have in windows (Admin , xxxxx)

---

### Post by Magneto on 2004-12-02
did you restart the samba services?
sudo smbd restart

---

### Post by Sniffer on 2004-12-03
Hi mag, you are the ubuntu man :)


I presume by your answer that everything that i have done it's correct and with my share security i don't need to create a samba user.


No i didn't have done that command..... the only thing i do it was the one above

/etc/init.d/samba restart


will try your tip, Thanks.

---

### Post by Magneto on 2004-12-03
hey i just reread your post and you did the equivalent of smbd restart
so its not the services
my mistake

---

### Post by bin on 2004-12-03
Add a user called Admin on your ubuntu machine - just a basic account, no frills just a member of users, then use:-

sudo -s
your ubuntu password

smbpasswd -a Admin
and put in the windows/smb password that is used on the window box

depends on what you want to be able to do from your windows machine as to how your smb.conf is set.

---

### Post by mr_ed on 2004-12-03
Yeah, but his access level is set to share, not user.  Once I did that, I was able to connect to my Ubuntu box with Windows machines.

(Of course, I wasn't able to write to those files since they had user "nobody."  :(

---

### Post by Sniffer on 2004-12-03
I was able to put samba fully working on Fedora Core 3....almost with the same settings as above.....

As many i'm really stucked with this...i will try to update to samba 3.0.8...maybe just work....

But first will try with user....let's see.... will post the results after.


Thanks for all the reply's.

---

