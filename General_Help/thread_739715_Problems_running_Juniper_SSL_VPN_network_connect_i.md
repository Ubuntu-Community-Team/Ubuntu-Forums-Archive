---
title: "Problems running Juniper SSL VPN network connect in Kubuntu 8.04 beta"
date: 2008-03-30
forum: General Help
---

### Post by ubunew1124 on 2008-03-30
I upgraded my Kubuntu 7.10 to 8.04 Beta. Juniper SSL VPN/network connect was working in 7.10 based on instructions in another thread esp. from madscientist. However after upgrading to 8.04Beta I have reached a point where the installNC.sh and xlaunchNC.sh don't give
any errors and I am prompted for password by xterm, but I don't
get the network connect window when it launches network connect.

Not sure if anyone tried installing network connect on 8.04 Beta.

--------------------------------
From java debug console: (after clicking on 'network connect')

=========
Launching "/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java" "-classpath" "/home/aman/.juniper_networks/network_connect/NC.jar" "NC" "-h" "sa.juniper.net" "-n" "" "-t" "" "-x" 
basic: New window ID: 0
basic: Stopping applet ... <--- why??
=========

See more details below:

The 2 'File not found/permission denied' errors below I presume are
 due to the juniper ssl code trying to copy installNC.sh and
 xlaunchNC.sh in the network_connect/ directory but which I have
 run 'chattr +i ' (making them immutable -since juniper scripts are bad)
 and the file copy fails which should not be of concern.

basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@73a7ab
basic: New window ID: 16016e9
basic: Value of xembed: 1
basic: setWindow: call before applet exists:16016e9
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=1
basic: Added progress listener: sun.plugin.util.GrayBoxPainter@6210fb
basic: Loading applet ...
basic: Initializing applet ...
basic: Starting applet ...
basic: Referencing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=2
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=1
Calling Super Init.
network: Connecting [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) with proxy=DIRECT
security: Loading certificates from Deployment session certificate store
security: Loaded certificates from Deployment session certificate store
network: Connecting [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) with cookie "DSSignInURL=/; DSID=57f99e9aefaed44e5d3059661acb0966; DSFirstAccess=1206851709; DSLastAccess=1206851738"
network: Server [https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar](https://sa.juniper.net/dana-cached/nc/ncLinuxApp.jar) requesting to set-cookie with "DSLastAccess=1206851740; path=/; Secure"
/home/aman/.juniper_networks
File not found 
java.io.FileNotFoundException: /home/aman/.juniper_networks/network_connect/installNC.sh (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
	at FileUtil.copyFile(FileUtil.java:188)
	at FileUtil.copyFile(FileUtil.java:176)
	at FileUtil.copyFile(FileUtil.java:171)
	at InstallNC.copyFile(InstallNC.java:43)
	at InstallNC.main_run(InstallNC.java:91)
	at SecureNCLauncher.RunTargetApp(SecureNCLauncher.java:251)
	at SecureLauncherApplet.startTargetApp(SecureLauncherApplet.java:358)
	at SecureLauncherApplet.doInstall(SecureLauncherApplet.java:214)
	at SecureLauncherApplet.start(SecureLauncherApplet.java:194)
	at sun.applet.AppletPanel.run(AppletPanel.java:420)
	at java.lang.Thread.run(Thread.java:595)
File not found 
java.io.FileNotFoundException: /home/aman/.juniper_networks/network_connect/xlaunchNC.sh (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:179)
	at java.io.FileOutputStream.<init>(FileOutputStream.java:131)
	at FileUtil.copyFile(FileUtil.java:188)
	at FileUtil.copyFile(FileUtil.java:176)
	at FileUtil.copyFile(FileUtil.java:171)
	at InstallNC.copyFile(InstallNC.java:43)
	at InstallNC.main_run(InstallNC.java:92)
	at SecureNCLauncher.RunTargetApp(SecureNCLauncher.java:251)
	at SecureLauncherApplet.startTargetApp(SecureLauncherApplet.java:358)
	at SecureLauncherApplet.doInstall(SecureLauncherApplet.java:214)
	at SecureLauncherApplet.start(SecureLauncherApplet.java:194)
	at sun.applet.AppletPanel.run(AppletPanel.java:420)
	at java.lang.Thread.run(Thread.java:595)
Here is the standard output of the command:

No difference found
Here is the standard error of the command (if any):

in get Proxy info..
No Proxy configured to for [http://sa.juniper.net/](http://sa.juniper.net/)
linux_start_script= 
linux_end_script= 
para 0 is /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java
para 1 is -classpath
para 2 is /home/aman/.juniper_networks/network_connect/NC.jar
para 3 is NC
para 4 is -h
para 5 is sa.juniper.net
para 6 is -n
para 7 is 
para 8 is -t
para 9 is 
para 10 is -x
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
liveconnect: JSObject::getMember: name=document
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
liveconnect: JSObject::getMember: name=cookie
liveconnect: the url of the applet is [https://sa.juniper.net](https://sa.juniper.net) and the permission is = true
DSID=57f9
Launching "/usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java" "-classpath" "/home/aman/.juniper_networks/network_connect/NC.jar" "NC" "-h" "sa.juniper.net" "-n" "" "-t" "" "-x" 
basic: New window ID: 0
basic: Stopping applet ... <--- why??
basic: Finding information ...
basic: Releasing classloader: sun.plugin.ClassLoaderInfo@157aa53, refcount=0
basic: Caching classloader: sun.plugin.ClassLoaderInfo@157aa53
basic: Current classloader cache size: 2
basic: Done ...
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter@6210fb
basic: Destroying applet ...
basic: Disposing applet ...
basic: Quiting applet ...
basic: Joining applet thread ...
basic: Joined applet thread ...

----------------------------------------------------

DIrectories:

.:
total 572
-rw-r--r-- 1 aman aman  48272 2008-03-29 21:35 dsHCLauncher_linux1.log
-rw-r--r-- 1 aman aman      6 2008-03-29 21:35 hcport.txt
-rw-r--r-- 1 aman aman 137845 2007-12-25 22:28 hostchecker.jar
-rw-r--r-- 1 aman aman 375118 2007-12-25 22:14 ncLinuxApp.jar
drwxr-xr-x 2 aman aman   4096 2008-03-29 21:35 network_connect
drwxr-xr-x 3 aman aman   4096 2008-03-29 21:35 tmp

./network_connect:
total 912
-rw-r--r-- 1 aman aman    329 2008-03-29 21:35 installnc.log
-rwxr--r-- 1 aman aman    730 2008-03-29 01:15 installNC.sh
-rw-r--r-- 1 aman aman 493680 2008-03-29 21:35 libncui.so
-rw-r--r-- 1 aman aman      0 2008-03-29 21:35 missing.info
-rwxr--r-- 1 aman aman  24888 2008-03-29 21:35 ncdiag
-rwxrwxrwx 1 aman aman  45478 2008-03-29 21:35 NC.jar
-rws--s--x 1 root root 332044 2008-03-29 01:16 ncsvc
-rw-r--r-- 1 aman aman     14 2008-03-29 01:16 version.txt
-rwxr--r-- 1 aman aman   1637 2008-03-29 01:12 xlaunchNC.sh

./tmp:
total 916
-rw-r--r-- 1 aman aman    770 2008-03-29 21:35 getx509certificate.sh
-rw-r--r-- 1 aman aman    716 2008-03-29 21:35 installNC.sh
-rw-r--r-- 1 aman aman 493680 2008-03-29 21:35 libncui.so
drwxr-xr-x 2 aman aman   4096 2008-03-29 21:35 META-INF
-rw-r--r-- 1 aman aman  24888 2008-03-29 21:35 ncdiag
-rw-r--r-- 1 aman aman  45478 2008-03-29 21:35 NC.jar
-rw-r--r-- 1 aman aman 332044 2008-03-29 21:35 ncsvc
-rw-r--r-- 1 aman aman     14 2008-03-29 21:35 version.txt
-rw-r--r-- 1 aman aman   1632 2008-03-29 21:35 xlaunchNC.sh

./tmp/META-INF:
total 12
-rw-r--r-- 1 aman aman 2952 2008-03-29 21:35 IMPORTED.RSA
-rw-r--r-- 1 aman aman  631 2008-03-29 21:35 IMPORTED.SF
-rw-r--r-- 1 aman aman  578 2008-03-29 21:35 MANIFEST.MF

---------------------------------------------
Scripts: 
xlaunchNC.sh
#!/bin/sh
# launch to install the service
# 20051220 : Javeed : Added -n to modprobe for dry run. We dont want to insmod, just check if tun
#                                               is available.

if [ "$#" -lt "1" ]
then
        echo "Insufficient number of params"
        echo "$0 <install dir> "
        echo "$*";
        exit
fi

#echo "$*";

#moved code from installNC.sh to here so that we call xterm only if needed.
flag=1

if [ -e "$1/ncsvc" ]
then
        if [ -e "$1/version.txt" ]
        then
                old_version=`grep -i "Version" $1/version.txt | cut -f 2 -d " "`;
                new_version=`grep -i "Version" $1/../tmp/version.txt | cut -f 2 -d " "`;
#               echo "$old_version == $new_version"
                if [  "$old_version" \< "$new_version"  ]
                then
                        echo "Need to install the new service"
                else
                        flag=0
                        echo "No difference found"
                fi
        fi
else
        echo "Service needs to be installed for the first time"
fi
if [ "$flag" -eq "1" ]
then
    echo "calling $1/installNC.sh"
    chmod 744 $1/installNC.sh
    `xterm -e $1/installNC.sh $1`
fi

#export LD_LIBRARY_PATH=/usr/X11R6/lib

# no need to check for ncui. Have to check for openssl package and tun driver.
#ldd $1/ncui | grep "not found" | tr -d "\t" | cut -d " " -f 1 | tee $1/missing_libs
# check if modprobe can locate the tun module.
#Adding dry run option we dont want to insmod, just check if tun is available

rm -rf $1/missing.rpt
/sbin/modprobe -n tun 1> $1/missing.info
if [ "$?" -ne "0" ]
then
    echo "Modprobe for Tun driver failed." > $1/missing.rpt
#    rpm -q tun 1> $1/missing.rpt
fi
#check if openssl is installed
#rpm -q openssl 1>> $1/missing.info
#if [ "$?" -ne "0" ]
#then
#    echo "RPM query for openssl failed." >> $1/missing.rpt
#fi

--------------------------------------------------
installNC.sh:
#!/bin/sh
# Install the service

if [ "$#" -lt "1" ]
then
        echo "Insufficiant number of parameters"
        echo "$0 <install dir>"
        exit;
fi

if [ -e "$1/ncsvc" ]
then
        echo "Service needs to be reinstalled."
else
        echo "Service needs to be installed for the first time."
fi

ok="try"
until [ "$ok" = "done" ]
do
        echo "Please enter the root/su password"
        su root -c "install -m 6711 -o root $1/../tmp/ncsvc $1/ncsvc"
        if [ "$?" -eq "0" ]
        then
                cp $1/../tmp/version.txt $1/
                ok="done"
                rm -rf $1/../tmp
        else
                echo "Invalid su password and/or Unable to install ncsvc"
                echo -n "Do you want to try again (enter y to try again):";
                read choice;
                if [ "$choice" != "y" ]
                then
                        ok="done"
                fi
        fi
done
chmod 744 $1/ncdiag
------------------------------------

Any help appreciated,

Thanks!
ubunew1124

---

### Post by kingtux on 2008-04-27
Same problem here!!! Trying to figure out whats going on...I"ll post if I find anything...U do the same

---

### Post by kingtux on 2008-04-27
This thread got me working again....
[http://ubuntuforums.org/showthread.php?t=515332&page=2](http://ubuntuforums.org/showthread.php?t=515332&page=2)

---

