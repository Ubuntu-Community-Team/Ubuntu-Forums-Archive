---
title: "Printer driver"
date: 2012-11-03
forum: General Help
---

### Post by offgridguy on 2012-11-03
I am having trouble installing the driver for my brother DCP7030 printer.
Is there a way to do this using the command line?

---

### Post by thnewguy on 2012-11-03
dpkg -i filename_of_driver.deb

---

### Post by ajgreeny on 2012-11-03
And if you haven't already got the drivers you can get them from
[http://www.brother-store.co.uk/category/brother-solutions-center_MjQyOA==.html](http://www.brother-store.co.uk/category/brother-solutions-center_MjQyOA==.html)

---

### Post by offgridguy on 2012-11-03
I appreciate the help, but this doesn't seem to work for me.I get this
Not Found

The requested URL /linux/en_us/download_prn.html was not found on this server.

Additionally, a 500 Internal Server Error error was encountered while trying to use an ErrorDocument to handle the request.



> **thnewguy said:**
> dpkg -i filename_of_driver.deb

All I get here is command not found.

Thanks anyway.

---

### Post by offgridguy on 2012-11-03
I have been trying the options available on the brother site, eg. below

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1c.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1c.html)

Not sure how to log in as sudo user ?   Frustrating because I have installed
the driver before once but  it's not so easy this time.  The problem is not getting it downloaded but installed.  :confused:

---

### Post by offgridguy on 2012-11-03
I found this quote by the very helpful Mark Phelps

> **Mark Phelps said:**
> 

A big difference between Linux and Windows is the ready availability of drivers -- and the ease with which they are installed.  EVERYONE makes Windows drivers, they usually come on the product CD, and installing them is usually just running a setup program from the CD.

Linux drivers, if they are found during setup, are installed automatically.  Some drivers are easily added after setup using Additional Drivers.  Other drivers are extremely hard, if not impossible, to hunt down and install -- because they often have to be built from scratch.

So basically, if you WANT to install apps from source code and/or build your own drivers from source code -- then Linux is going to be a STEEP learning curve -- because there's really no equivalent to doing this in MS Windows.

However I did have this printer working once, but due. to a recent reinstall
I lost that,  the procedure I used last time doesn't seem to want to work this time. :confused:

---

### Post by offgridguy on 2012-11-03
Here is the procedure I was given last time, What am I missing?
> 
 Re: printer
You don't need to use the CLI to extract the file. If you find the file with Nautilus and right-click it, you should be able to extract it. Just remember where you put it. The actual script does need to be run from the command line. You need to do this from an account with sudo or 'administrator' privileges. I saved the file 'linux-brprinter-installer-1.0.4-1 to Desktop. I then extracted it and got a file by the same name. Open a terminal and enter "cd Desktop" then "dir". You should see the file listed. At that point you can type in the terminal "sudo bash linux-brprinter-installer-1.0.4-1". (Cheat-hint: right-click copy and paste work in terminal) It should then ask you for the model. Enter something like "MFC-7030" and yes, letter case does matter. At that point the script should run, ask for a couple "do you agree?" questions, ask what kind of connection etc. etc.

At the point where this says you should see the file listed.  It doesn't.  Apparently there is no way to use the GUI for installing a Brother printer driver.
Tommorrow is another day, I will try again then.

---

### Post by ajgreeny on 2012-11-04
> **offgridguy said:**
> I appreciate the help, but this doesn't seem to work for me.I get this
Not Found

The requested URL /linux/en_us/download_prn.html was not found on this server.
For some reason that URL reported to you is not the one I linked to which certainly does work.  Were you sent to the site you show even though you clicked on my link?

---

### Post by BlinkinCat on 2012-11-04
> **ajgreeny said:**
> For some reason that URL reported to you is not the one I linked to which certainly does work.  Were you sent to the site you show even though you clicked on my link?

Hi,

I got a "you do not have permission" error on that link too.
Hope that helps - :)

---

### Post by ajgreeny on 2012-11-04
So can you get to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030) to get the .deb driver package?

If you can all you need to do is double click on it once downloaded and it should install.

Similarly the scanner driver should be available from either
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-5.amd64.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-5.amd64.deb&lang=English_gpl)
for 64 bit, or
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brscan3-0.2.11-4.i386.deb&lang=English_gpl)
for 32 bit.

---

### Post by offgridguy on 2012-11-04
> **ajgreeny said:**
> So can you get to [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-7030) to get the .deb driver package?

If you can all you need to do is double click on it once downloaded and it should install.



Thank you for the reply,  I think the operative word here is_ should  _install.  I haven't found a way to do this using the GUI.
     The last time I installed a brother printer driver I ran the install script in a terminal
with sudo privileges .
I can download the script, have it open in text editor beside the terminal,type in all the commands from the brother page, or the commands I had from the last time I did this
but no luck yet,  all i get is no such file or directory, or command not found.  I am missing something obviously.
   I wish I could do it using the GUI.](*,)

---

### Post by kurt18947 on 2012-11-04
> **offgridguy said:**
> Thank you for the reply,  I think the operative word here is_ should  _install.  I haven't found a way to do this using the GUI.
     The last time I installed a brother printer driver I ran the install script in a terminal
with sudo privileges .
I can download the script, have it open in text editor beside the terminal,type in all the commands from the brother page, or the commands I had from the last time I did this
but no luck yet,  all i get is no such file or directory, or command not found.  I am missing something obviously.
   I wish I could do it using the GUI.](*,)

Yes, the script does require using the command line.  I've had very good luck using it and being able to execute a BASH script is a useful skill to have.  Are you able to download the script?  If so, I extract it to the desktop of an account with SUDO privileges.  By default, that's the first account you established when you installed.  If you have trouble downloading the script, PM me and I can attach it or email it or something.  

Once you have the script in text form on the correct desktop e.g. an account with SUDO privileges, open a terminal and type:

cd Desktop
dir
You should see the script file listed there,** linux-brprinter-installer-1.0.4-1**
At this point you could cheat a little:).  Copy and paste via the right mouse button work in the terminal.  Type the following:

"sudo bash" then copy/paste the file name.  Copy/paste can save typos.  The entire line should read "sudo bash linux-brprinter-installer-1.0.4-1"   Press "enter".  You'll be prompted for your password.  Type it in, there's no feedback like *****,  just type the password and press "enter".  The script should start.  Enter model using caps etc. etc.

---

### Post by offgridguy on 2012-11-04
Hello kurt18947;  Thank you for coming in here, you helped me the last time i did this,very
much appreciated.  I have some new info on brother printer drivers here.

[http://myubuntux.wordpress.com/2011/02/21/brother-printer-drivers-ubuntu-linux/](http://myubuntux.wordpress.com/2011/02/21/brother-printer-drivers-ubuntu-linux/)

I have followed this through to this point.  " You will then find the driver in System>
Administration>Printing.  Select it and print a test page. Done.
   How do I access this?
System>Administration>Printing

If this works it will be the only method i have found using the GUI,  But either way I have to learn it as I intend to try other distro's , so i will need it again.
Thank's again. :)

---

### Post by ajgreeny on 2012-11-04
> **offgridguy said:**
> Thank you for the reply,  I think the operative word here is_ should  _install.  I haven't found a way to do this using the GUI.
     The last time I installed a brother printer driver I ran the install script in a terminal
with sudo privileges .
I can download the script, have it open in text editor beside the terminal,type in all the commands from the brother page, or the commands I had from the last time I did this
but no luck yet,  all i get is no such file or directory, or command not found.  I am missing something obviously.
   I wish I could do it using the GUI.](*,)
So having downloaded the brother .deb files from that site what happens when you double click on them?  You are still talking about a script, which should not be needed to install a .deb package.

In past Ubuntu versions gdebi would open and install them, dragging in any dependencies you didn't already have.  At some point gdebi was removed from the default install and software centre did the job, but gdebi could still be added, and I always did so.  I have no idea if gdebi is available in `12.10, but it certainly is in 12.04.

---

### Post by offgridguy on 2012-11-04
A double click takes you to the software center where you have the install option, click on
that and it doesn't install, I tried several times , same result.

---

### Post by cyncicle on 2012-11-04
Try reading through this thread:

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

Hope it helps!

---

### Post by offgridguy on 2012-11-04
> **cyncicle said:**
> Try reading through this thread:

[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)

Hope it helps!

Thanks for the reply, nothing real new here though. :D

---

### Post by offgridguy on 2012-11-05
I appreciate all the offers to help, but i have spent to much time on this
already.  I give up.
Will be marked as solved.

---

### Post by oldos2er on 2012-11-05
The 'Solved' tag exists to help others with the same problem find a solution. Since your issue is not solved, please don't mark the thread as such.

---

### Post by ajgreeny on 2012-11-05
> **offgridguy said:**
> A double click takes you to the software center where you have the install option, click on
that and it doesn't install, I tried several times , same result.
So what does happen?  Any errors shown?
Put the .debs in a newly made folder then run ```
cd *newfolder*
sudo dpkg -i *.deb
``` and report any errors.

---

### Post by offgridguy on 2012-11-06
> **oldos2er said:**
> The 'Solved' tag exists to help others with the same problem find a solution. Since your issue is not solved, please don't mark the thread as such.

My apologies, I didn't know this, thank you for the clarification. :)

---

