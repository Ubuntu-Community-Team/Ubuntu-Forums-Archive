---
title: "Connectivity conundrum"
date: 2007-10-25
forum: General Help
---

### Post by grEnAlEins on 2007-10-25
I am in quite a pickle.  My school requires the use of a Java Applet to connect to the school's network(s).  I downloaded Java from Java.com onto a thumb drive and put it on the desktop of my Linux laptop.  I tried to follow the directions from Java.com, but had no luck.  I tried to move the file to a different directory (tried /user/java and /usr/local) and it would not let me copy the install file there.  I figured that this would make the install possible, as the directions had me run commands from those directories.

The instructions I used are here:

------------------------------------------------------------------------------
 To install the Linux (self-extracting) file

Follow these instructions:

   1. At the terminal: Type:
      su
   2. Enter the root password.
   3. Change to the directory in which you want to install. Type:
      cd <directory path name>
      For example, to install the software in the /usr/java/ directory, Type:
      cd /usr/java/

      Note about root access: To install the JRE in a system-wide location such as /usr/local, you must login as the root user to gain the necessary permissions. If you do not have root access, install the JRE in your home directory or a subdirectory for which you have write permissions.
   4. Change the permission of the file you downloaded to be executable. Type:
      chmod a+x jre-6u2-linux-i586.bin
   5. Verify that you have permission to execute the file. Type:
      ls -l

Make sure the installation file has executable permission

   6. Start the installation process.Type:
      ./jre-6u2-linux-i586.bin

      This displays a binary license agreement. Read through the agreement. Press the spacebar to display the next page. At the end, enter yes to proceed with the installation.

type YES to agree to the license agreement

   7. The JRE is installed into its own directory. In this example, it is installed in the /usr/java/jre1.6.0_02 directory. When the installation has completed, you will see the word Done.

The installation completes

   8. The JRE is installed in jre1.6.0_02 sub-directory under the current directory. In this case, the JRE is installed in the /usr/java/jre1.6.0_02 directory. Verify that the jre1.6.0_02 sub-directory is listed under the current directory. Type:
      ls

Verify the installation filename

The installation is now complete. Skip to the Enable and Configure section. 

---------------------------------------------------------------------------

Am I using the right type of file? It is a ".bin".  I had installed shockwave and flash in the past using a ".tar.gz" file and was expecting the same.  Should I use the ".rpm" file instead?  Another type?

Does anybody know what I should do?

Thanks,

Nick:biggrin:

---

### Post by Shazaam on 2007-10-25
Read this...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by grEnAlEins on 2007-10-25
> **Shazaam said:**
> Read this...
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
I read it.  I was and am able to execute the file.  The issue is that it will not let me move the file to anywhere in the /usr folder.  I apparently do not have write privileges in the folder.  If I run the installer from the desktop, it installs a to my desktop.  I tried connecting with this installed on the desktop and had no such luck.  When I try to connect to the school's network it says that I need to install a java plug in.  I click either a hyperlink to where I can download from, or click a button that says install missing plugins.  I cannot follow the url, as I am not able to access the internet, and Firefox cannot detect any available plugins.

What do I need to do in order to install this in the appropriate place?  Is there a better place to install besides in the /usr/java or /usr/local directories?

---

### Post by grEnAlEins on 2007-10-25
Issue resolved in class today, and my wireless works--although not perfectly.

---

