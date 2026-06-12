---
title: "Login in loop problem"
date: 2016-06-03
forum: General Help
---

### Post by Beexo on 2016-06-03
Hi all,

I normally don't ask for help unless I have tried all to the best of my knowledge.

I have installed Ubuntu 16.04 LTS fresh a few days ago. All was working fine. Now I cannot login. Always comes back to the login screen. 

What I am able to do: I can login in a terminal (Ctrl+Alt+F1). I can login with guest in GUI.

What I am not able to do: I cannot login with my user in GUI.

What I have tried: 
1- I have renamed .Xauthority to .Zautority.back. Did not work. It does not create a new .Xauthority file.
2- Did "apt update" and "apt upgrade". 
3- Did "chown $USER:$USER .Xauthority. 
4- Removed lightdm; Installed lightdm; dpkg-reconfigure lightdm. 
5- Did mokutil --disable-validation
6- Did chmod a+wt /tmp. This was unnecessary because I have moved /tmp to RAM to save on read and writes on the SSD. Wondering now if this could be a problem.
7- Tried unity --reset but did not do anything.
8- Ran the "sgfxi" script as suggested by some.
service lightdm stop
sudo su -
cd /usr/local/bin
wget -Nc smxi.org/sgfxi
chmod +x sgfxi
sgfxi

None of the above resolved the login problem and I am now without ideas.

The motherboard is an Asus Z170 pro. Therefore it has the Intel graphics. There is nothing nvidia on this machine.

The last thing I did before a restart and when this problem occurred: I have an extra disk. So I was encrypting the disk with LUKS. 
1- I created a file called "key" in /root
2- Encrypted the disk with the key file
3- I mapped the LUKS container to a file called "Disk1"
Then I rebooted. Typed the password as usual and the login prompt came back. Tried one more time and the same thing happened. My head almost exploded.

Please, help me overcome this issue.

Update: I created another user and also this user cannot login.

Update: So, I installed KDE Desktop. When logging in to it, I get "$HOME directory is out of disk space".
"df" shown that /home is 100% used.
I deleted some files I didn't need, but still shows 100% used.
My /home is on a partition by itself and is encrypted.
To me this doesn't seem normal. Also, I don't know if this is causing the problem with the login. But I am not sure and also don't know what to do. Your help is appreciated.

Update: Since I had the other disk I was setting up with ZFS on top of LUKS, I decided to finish the job, which I did. Then I copied my "/home" to this new disk. I deleted some more stuff from my "/home" partition, and this time "df" shows it at 74% used. This means I have about 50GB free space now.
I went back to the desktop (Ctrl+Alt+F7) typed the password and Boooooom, it logged in with no problem.
I can only associate this problem with the SSD. Anyway all I have to do now is map "/home" to the one on the new disk and pray that it works.

Update: I have now mounted "/home" to the new disk. I have rebooted the machine and it is still working. I now have 140GB of free disk space for "/home".

---

