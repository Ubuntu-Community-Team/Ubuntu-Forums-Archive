---
title: "Aurorun"
date: 2007-01-03
forum: General Help
---

### Post by rmartz on 2007-01-03
I am looking for instructions to setup a CD with autorun functions similar to autorun.inf in Windows. It is possible, and where would I find somewhat understandable instructions.

Thanks. Loving Ubuntu.

---

### Post by meng on 2007-01-03
Can you elaborate on what you're trying to get to run automatically?

---

### Post by rmartz on 2007-01-03
I would like it to call up a html file on the CD.

---

### Post by rmartz on 2007-01-05
I have searched the net and found instructions for other versions of linux. None seem to work with Ubuntu. They stated that "exec" needed to be added to the fstab file line controlling the cdrom, which I did. 

I was then instructed to create an "autorun" file with a few various scripts. I tried them all. None seemed to work.

I tried the call up the "htmlview" command. Nothing. I even tried to exec firefox Page.html from within the script. It didn't work. I executed the line in the terminal, it worked just fine. 

Any more suggestions?

---

### Post by rmartz on 2007-01-10
I am assuming from the lack of response that there is no response to the autorun issue at this time.

Is there another place for me to continue to inquire?

---

### Post by Johnsie on 2007-01-10
I'm not sure but I think autorun may have been disabled to prevent unknown codes/programs being executed. Autorun is a major security risk on windows. I'm interested to see if you can find a way of doing this though.

---

### Post by rmartz on 2007-01-11
I assumed that it has been disabled. I just figured there would be a way to reenable it. This way I can make the choice if I want this secured or not. Seems like that choice is being taken away from me. I guess I am only being allowed certain freedoms. I know the system and setting that I would like to use the Autorun. I am dealing with a CD with about 150 hmtl files. All I want to do is start ONE html file. I may have to look at installing an older version of Windows since this system is being used by a historical society that just needs it to view a few html files and old photos. 

So where does one go to get an "Official answer" to my question? I had hoped I would get a clear yes or no. I appreciate the couple of responses, but where do i go to get a definate answer?

---

### Post by Buck2348 on 2007-01-11
I don't know if it could be this easy after your efforts at finding a solution, but have you tried:  System --> Preferences --> Removable Drives and Media --> Storage tab --> Autorun programs on new drives and media?

Regards,
Buck

---

### Post by rmartz on 2007-01-11
I turned on this setting, but still was unable to get an autorun.

I created a text file named "autorun" then renamed it "autorun.sh" then renamed it "Autorun" with none working. Within the autorun file I have posted several different command lines. The one I have left in is the command line I could get to activate in the terminal:

#!bin/sh
exec firefox Page.html

The file is just not being triggered. So something is shutting it down. Several other versions of linux allow for the autorun. Something is not allowing it to run at CD insertion. 

I will en devour to persevere.

---

### Post by Buck2348 on 2007-01-12
How about Applications --> System Tools --> Configuration Editor --> desktop --> gnome --> volume_manager --> autorun?

Buck

---

### Post by rmartz on 2007-01-12
I HAVE CRACKED THE CODE!!

I think I know how the guy on DaVinci Code felt, although I only enjoyed it for it's entertainment value. There was very little fact in all the fiction.

Okay, back to the autorun topic.

Buck, your direction to the:

System --> Preferences --> Removable Drives and Media --> Storage tab --> Autorun programs on new drives and media

Was right on. This parallels the setting your suggested later at:
Applications --> System Tools --> Configuration Editor --> desktop --> gnome --> volume_manager --> autorun

Yet, this last suggestion gave me the clue I needed. I found the three file types that can become autoruns. They are .autorun:autorun:autorun.sh

So I took the scripts I found on line for other versions of linux and started to work. 

Okay, here are the final steps, although I went through many until I finally figured this all out. I am sure some linux geek will read this and say, "I knew that." but I could not find this info anywhere, nor would anyone pass on this info. Okay, I will quit whining and start telling.

Step 1:
System --> Preferences --> Removable Drives and Media --> Storage tab --> Autorun programs on new drives and media (Thanks Buck)

Step 2:
create a text file with gedit or the like called autorun (or .autorun or autorun.sh)

In this text file, I had to remove the first line that every other version of linux seemed to need: #!/bin/sh  Don't use it. Don't let temptation take you. It will not work. After 30 plus CD burns, I know. (I was using a CD-RW so don't flame me for filling up the local landfill. ;)

To start up a html file, all I had to do was have one line in the file:

firefox Page.html

Save the file

Step 3:
Right click on the autorun file you saved then click Properties.
Click the Permissions Tab.
Check the "Execute: Allow executing file as program
Click Close

Step 4:
Burn this and the html file you stated in the autorun file.

Step 5:
Open then close the CD drawer. (If you use the button in the CD burner instead of right clicking on the CD icon on the desktop, you will get griped at for doing a very unsafe thing. I would love to find a way to shut off that warning.)

Step 6:
Once the CD spins up, it should show up on the desktop. A few seconds afterwards, you should get a little box that states there is an autorun file and you have an option of "Ignore" or "Auto-run".

Step 7:
Click Auto-run!!! well unless you want to ignore it like I am usually ignored. ;)

Hope that helps anyone else who is looking for a simple way to autorun a html file from a CD.

Now, I can complete my CD with an autorun.inf for Windows and an autorun for Ubuntu and it will pull up my html file on either. I know there is a way to add a Mac autorun, but I will wait until someone with a Mac screams at me.

Peace.

---

### Post by Buck2348 on 2007-01-13
Cool.  Good job--glad you were able to fix it.

Buck

---

