---
title: "Odd ./INSTALL error"
date: 2007-07-31
forum: General Help
---

### Post by Astromike on 2007-07-31
Hello!

I am currently trying to install some software and I enter the correct commands, then software starts to install, then I get this error:

./Spitzer-pride16_0_3-linux.sh: 28: ./INSTALL: not found


Has anyone seen an error like this? This is my 3rd time installing this software and have never had this issue.

the full dialog is here:
```

root@michael-desktop-Linux:/home/michael/Spitzer# ./Spitzer-pride16_0_3-linux.sh
Unpacking...
Extracting...
INSTALL
./
./._.DS_Store
./.DS_Store
./._activation.jar
./activation.jar
./._archive_common.jar
./archive_common.jar
./._archive_dto_irsa.jar
./archive_dto_irsa.jar
./._archive_dto_query.jar
./archive_dto_query.jar
./._archive_dto_votable.jar
./archive_dto_votable.jar
./._archive_ws_common.jar
./archive_ws_common.jar
./._ArchiveRetrieve-client.jar
./ArchiveRetrieve-client.jar
./._ArchiveSearch-client.jar
./ArchiveSearch-client.jar
./._ArchiveSecurity-client.jar
./ArchiveSecurity-client.jar
./._astro.jar
./astro.jar
./._axis.jar
./axis.jar
./._client.jar
./client.jar
./._client_sysfiles.jar
./client_sysfiles.jar
./._commons-discovery-0.2.jar
./commons-discovery-0.2.jar
./._commons-logging-1.0.4.jar
./commons-logging-1.0.4.jar
./crimson.jar
./._data.jar
./data.jar
./._fits.jar
./fits.jar
./._InterfaceToMac.jar
./InterfaceToMac.jar
./._iText_light.jar
./iText_light.jar
./._javaftpapi.jar
./javaftpapi.jar
./jaxp.jar
./._jaxrpc.jar
./jaxrpc.jar
./._jcommon-1.0.5.jar
./jcommon-1.0.5.jar
./jcpagelayout.jar
./._jfreechart-1.0.2.jar
./jfreechart-1.0.2.jar
./._jhall.jar
./jhall.jar
./._jsr173_1.0_api.jar
./jsr173_1.0_api.jar
./._leopard.jar
./leopard.jar
./loader.jar
./._mail.jar
./mail.jar
./meta.jar
./._oldsodb.jar
./oldsodb.jar
./._planner.jar
./planner.jar
./._saaj.jar
./saaj.jar
./._simbad_ws.jar
./simbad_ws.jar
./._sodb.jar
./sodb.jar
./._subscriber.jar
./subscriber.jar
./._sut.jar
./sut.jar
./._suthelp.jar
./suthelp.jar
./._uplink_util.jar
./uplink_util.jar
./._uplink_vis_client.jar
./uplink_vis_client.jar
./._wsdl4j-1.5.1.jar
./wsdl4j-1.5.1.jar
./._xbean.jar
./xbean.jar
./
./._.DS_Store
./.DS_Store
./._Leopard_ReleaseNotes_v7.pdf
./Leopard_ReleaseNotes_v7.pdf
./._Leopard_ReleaseNotes_v7.txt
./Leopard_ReleaseNotes_v7.txt
./._Spot_ReleaseNotes_v16.pdf
./Spot_ReleaseNotes_v16.pdf
./._Spot_ReleaseNotes_v16.txt
./Spot_ReleaseNotes_v16.txt
jre.tar.gz
cleaning up...
installing...
./Spitzer-pride16_0_3-linux.sh: 28: ./INSTALL: not found
```

---

### Post by lynxus on 2007-07-31
Ignore what i said b4 about it not extracting INSTALL lol.


Altho looking at most of teh files they appear to be java files? 
As far as i know you dont "install" them, you need to run i like a script?

Try sudo chmod +x INSTALL   

?
then ./INSTALL

---

### Post by ivanmladek on 2008-02-12
I second that, I get an identical error on my 64bit gutsy machine. What to do?

---

### Post by ivanmladek on 2008-02-12
try running the [COLOR="Red"][windows version ]("http://ssc.spitzer.caltech.edu/propkit/spot/software/S17.0.2/Spitzer-pride17_0_2-windows.exe")[/COLOR]with [COLOR="Red"][wine ]("http://www.winehq.org/site/download-deb")[/COLOR] which worked for me

---

### Post by sdhoigt on 2008-02-23
What is on line 28 of Spitzer-pride16_0_3-linux.sh?

SD

---

### Post by darenw on 2008-06-21
I downloaded v18 of the pride. installed okay on an Ubuntu 7.04 machine, but failed with the ./INSTALL complaint on a 7.10 machine.  


line 28 (for ver 16 as well as ver 18):
(cd $tempdir; ./INSTALL)

I suspect INSTALL is supposed to be an environment var that somehow didn't get defined.  Guessing that it should be defined as /usr/bin/install, i still got the error. 

How many Ubuntu users in the world are using the Spitzer software?

---

### Post by lynxus on 2008-06-27
./INSTALL is normally just a file that you are executing with .

do a ls -l to see the permissions of the files.

INSTALL should be there with the X value.

if not try.. chmod +x INSTALL


Maybe this will help? i dont know. but thought id drop my 2c in.

---

### Post by darenw on 2008-06-28
Ah, sweet success! I had time to study the the Spitzer .sh file.  The first several lines are a shell script to make a copy of the whole file, minus the first 31 lines, and naming this copy as a .tar file.  Then tar is used to extract actual files.  I ended up doing this manually.

One of the extracted files is INSTALL, which is a C shell script. Turns out i didn't have C shell installed.  A quick "apt-get install csh"  took care of that.   That long list of files shown in the OP's output dump is the tar being extracted. But upon failing to execute INSTALL, the initial self-extracting script notices and deletes the whole mess of files.  So, no INSTALL file ever appears to us mortals, along with a highly visible absence of any clues.  Well, some of us mortals are *evil* and can twist arms of shell scripts!

Off the topic of the original problem but closely related... I also had troubles with env vars named JAVA_HOME and CLASSPATH.  Neither is defined by Ubuntu's default setup, even if you had installed java with the package manager.  Turns out Ubuntu installs java in an odd way making it impossible (or very hard?) to set these vars in a way that works.   It so happens i had installed a genuine JDK (v1.6) installed in /usr/local, allowing these env vars to be set in .bashrc (remember to export, of course).  Then ./INSTALL rean just fine, stopping only once to ask for a path where to install the running version of the Spitzer pride software.

(IANJE = I Am No Java Expert; please excuse and correct any foolishness i say.)

---

