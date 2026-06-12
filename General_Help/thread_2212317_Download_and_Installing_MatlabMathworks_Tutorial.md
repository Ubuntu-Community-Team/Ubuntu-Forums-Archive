---
title: "Download and Installing Matlab/Mathworks Tutorial"
date: 2014-03-20
forum: General Help
---

### Post by austinhermann531 on 2014-03-20
I know that some people have trouble with installing Matlab through downloaded files, so this tutorial covers a method to install Mathworks along with potential problems and tips not covered in the Mathworks installation guide for the Linux OS. Unfortunately, depending on which version of Java installed on the computer along with a variety of other factors dictates how you install Mathworks. That being said, this procedure will successfully install Mathworks regardless of Java versions or other software factors.  

 

 1) To begin with, open a new Terminal window to check if and which version of Java runs on the computer by running the following script.
 

 [COLOR=#ff0000]username:~$ java -version
[/COLOR]
 

 
[LIST=1]
[*]If Java is not installed, go     install it. I would recommend Java 7 as it works better with     Mathworks. The other option is to manually compile and download the     individual files 
[*]If Java 1.6 or 1.7 is on the     computer, then continue following the installation guide. 
[/LIST]
 

 2) Retrieve the R2013a download agent from your Mathworks account. Under the manage licenses page there is a download option. Simply follow the steps to download the Linux OS download agent.
 

 3) Some web browsers will download the file as download_agent. Go into the properties under the basic tab and change the file name to   download_agent.jnlp    Then go under the permissions tab and check the &#8220;Allow executing file as program&#8221; box. The download agent has a Java script and the .jnlp allows the script to be read by Java. The checked box will allow the script to be executed in the terminal in step 4
 

 4) Re-open the Terminal and type the following:  
 

 [COLOR=#ff0000]username:~$ cd Downloads[/COLOR] (hit enter)       This will direct the Terminal to the downloads directory
 [COLOR=#ff0000]username:~$ javaws download_agent.jnlp[/COLOR] (hit enter)    This will execute the download agent with Java  
 

 Follow the Mathworks installation program and remember where the files are saved. I would recommend saving them to /tmp though (the default directory path). Then wait for the files to download. Also, do not unzip any files. The files are encrypted and only the installer script can successfully extract them.
 

 5) Once downloaded click finish and follow the Mathworks installation program. Make sure to check the bubble to &#8220;install with the internet&#8221;. This will allow Mathworks to automatically bring up your license you added on their website. Should Mathworks finish the download program but not open an installation program go to           /tmp/mathworks_downloads/R2013a          and extract       
         matlab_R2013a_glnxa64_installer.zip       into the same folder; this will not effect the installer. Re-open the terminal from step 4 and type the following:
 

 [COLOR=#ff0000]username:~$ cd[/COLOR] (hit enter)                                  This will bring the terminal back to the user directory
 [COLOR=#ff0000]username:~$ cd /tmp[/COLOR] (hit enter)
 [COLOR=#ff0000]username:~$ cd mathworks_downloads[/COLOR] (hit enter)     These steps are designating the script directory  
 [COLOR=#ff0000]username:~$ cd R2013a[/COLOR] (hit enter)
 [COLOR=#ff0000]username:~$ ls[/COLOR] (hit enter)                                      Lists the files to make it easy to retype them
 [COLOR=#ff0000]username:~$ matlab_R2013a_glnxa64_installer/install -v [/COLOR](hit enter)  Executes the installer
 

 The -v puts the Terminal into verbose mode which alerts the user if there was an error.
 6) The installation path can be tricky, however it generally is one of two options. The first is the default which is      /usr/local/bin/MATLAB/R2013a     If this folder fails to generate than it is most likely because of which directory the Terminal is referencing which is usually the user directory. If this occurs, then type the following        /home/username/usr/local/bin/MATLAB/R2013a       The username will be your username/profile name. For example my username is immortaldoor, so my directory path is        /home/immortaldoor/usr/local/bin/MATLAB/R2013a
 

 7) Make sure to check the box &#8220;Create symbolic links to MATLAB scripts in&#8221; . Use the same directory path as in step 6. Then finish the installation; don't worry about the optional additional steps at the end, they don't effect Matlab.
 

 8) This step pertains to installing the license file for the software. Again, depending on your Java versions and other software the installation file may or may not come with the download. If it does then the activation program will activate the license and there is nothing more needed. If a license file did not come with the download then the program will direct you back to the Mathworks website where the license.lic file can be downloaded. Simply move it into the same folder/directory as Matlab. Add the same directory path as in step 6. Also, just for housekeeping I would recommend moving the download_agent.jnlp script into the matlab folder as well to keep everything in one place.
 

 9) When opening Matlab there are a variety of methods, but the one that works regardless is by double clicking on the Matlab script and running it in the Terminal. This will run the program in the Terminal, however it will have the same GUI as any other method.  
 

 Common Problems when Installing Mathworks
 

 
[LIST=1]
[*]When you run the installer and get     the error &#8220;There are no products to install from this location&#8221;.     There are two main causes, the first being not all of the files were     downloaded. Try re downloading Mathworks or if you manually     downloaded all of the files make sure they are all there. The other     cause is a few of the folders were extracted. Make sure none of the     downloaded folders were extracted because only the installer can     extract them 
[*]When running the     download_agent.jnlp script and you get an &#8220;xml formatting error&#8221;     try downloading a different version of Mathworks. The one that works     is R2013a. 
[*]Make sure the download_agent is         download_agent.jnlp     so Java can read the script 
[*]Only extract the        matlab_R2013a_glnxa64_installer.zip    if needed. 
[*]Java 7 works better than Java 6,     however the previous procedure works for both.



hope this helps,

ImmortalDoor 
[/LIST]

---

