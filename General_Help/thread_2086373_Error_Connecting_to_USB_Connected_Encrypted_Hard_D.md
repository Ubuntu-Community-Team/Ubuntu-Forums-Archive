---
title: "Error Connecting to USB Connected Encrypted Hard Drive"
date: 2012-11-20
forum: General Help
---

### Post by FreeSW4TW on 2012-11-20
Hi All,

I'm trying to retrieve some data off of my last computer IDE Hard Drive (HD).  Some other H/W unceremoniously went "kaput" rendering my last computer unbootable.

The computer was dated, so I bought another computer and now I want to retrieve some data off my old HD.  I'm currently booting Ubuntu variant Mint 13 on my new computer. 

Here is what I've done so far:

1. Moved HD jumper to Cable Select.  I'm not sure if this is right or not.  I read that I want the HD to be in slave mode, but that wasn't specifically addressed on my HS label.

2. Hooked up up the HD to an IDE to USB kit and plugged it into my new computer.

3. The good news is that the HD works.  I chose the correct auto-mounted partition and went to my home directory.

4. I right clicked and chose ""log in as Administrator" (or similar nomenclature).

5. I'm presented with an icon named "Access-Your-Private-Data.desktop" and I chose it.

The problem becomes apparent at this point.

I get the following error:

"There was an error launching the application

Details: Failed to execute child process "xterm" (No such file or directory)"

So I'm stuck for the time being.

Any help is very much appreciated.

TIA...

---

### Post by Mark Phelps on 2012-11-20
Not familiar with the details you present -- as these are the Ubuntu forums, not the Mint forums ...

But anyway, in Ubuntu, you would simply click the "house" icon in the launch panel on the left and then double-click the icon for the filesystem you want to open.

Suggest that if you want Mint-specific instructions, you go to the Mint forums.

---

### Post by FreeSW4TW on 2012-11-20
> **Mark Phelps said:**
> Not familiar with the details you present -- as these are the Ubuntu forums, not the Mint forums ...

But anyway, in Ubuntu, you would simply click the "house" icon in the launch panel on the left and then double-click the icon for the filesystem you want to open.

Suggest that if you want Mint-specific instructions, you go to the Mint forums.

Hi Mark, I tried to be concise, but I left out that the encrypted HD is running Ubuntu 9.10, so it is kind of a hybrid problem.

I would gladly boot Ubuntu if I thought it could fix the problem.  Is double clicking supposed to work for encrypted HDs as well?  If so, I'll boot Ubuntu and give it a shot.

Thanks.

---

### Post by varunendra on 2012-11-21
> **FreeSW4TW said:**
> 
1. Moved HD jumper to Cable Select.  I'm not sure if this is right or not.  I read that I want the HD to be in slave mode, but that wasn't specifically addressed on my HS label.Doesn't matter if you are connecting via a USB adapter.

> **FreeSW4TW said:**
> 4. I right clicked and chose ""log in as Administrator" (or similar nomenclature).Didn't get this point. Were you trying to boot the older HDD which gave you that option ? Or is it some option in Mint (have used Mint 9/10, but not with encrypted directory)

Regardless of the error, if all you want is to decrypt your older data and copy it to your new computer, see if these are helpful -
[Manually recovering Encrypted Data]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Data_Manually")
or
[Opening Encrypted Home directory from Live CD]("https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory")

---

