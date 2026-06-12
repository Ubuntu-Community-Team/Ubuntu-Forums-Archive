---
title: "Installing Maya 2014 on Ubuntu 13.04"
date: 2013-05-30
forum: General Help
---

### Post by niallcd on 2013-05-30
I'm hoping to get a little help here installing the newest version of AD Maya 2014 on 13.04. I used this script to install it on the off chance it would work. 

*note: if there are problems with the script perhaps someone could provide a hand in fixing it so that we can ensure others have an easier time installing Maya on their systems. 

Script source: [https://gist.github.com/insomniacUNDERSCORElemon/5555214](https://gist.github.com/insomniacUNDERSCORElemon/5555214)

```
#!/bin/bash
#Heith Seewald 2012
#Feel free to extend/modify to meet your needs.
#Maya on Ubuntu v.1
#This is the base installer... I’ll add more features in later versions.
#if you have any issues, feel free email me at heiths@gmail.com
 
#this version is updated by insomniac_lemon... issues were fixed and it has been converted to 2014, use at your own risk... 
#testing in a VM first is recommended... (at least until I test it again or someone confirms it works without tinkering)
 
#### Lets run a few checks to make sure things work as expected.
#Make sure we’re running with root permissions.
if [ `whoami` != root ]; then
    echo Please run this script using sudo
    echo Just type “sudo !!”
    exit
fi
#Check for 64-bit arch
if [uname -m != x86_64]; then
    echo Maya will only run on 64-bit linux. 
    echo Please install the 64-bit ubuntu and try again.
    exit
fi
 
#Setup a few vars
export INSTALL='mayaTempInstall'
export RPM_INSTALL_PREFIX=/usr
export LD_LIBRARY_PATH=/opt/Autodesk/Adlm/R5/lib64/
LIBCRYPTO="/usr/lib/x86_64-linux-gnu/libcrypto.so.10"
LIBSSL="/usr/lib/x86_64-linux-gnu/libssl.so.10"
URL="http://trial.autodesk.com/SWDLDNET3/2014/MAYA/ESD/Autodesk_Maya_2014_English_Linux_64bit.tgz"
 
#Install Message
echo "You’re about to download and install Autodesk Maya 2014"
echo ""
echo "Do you wish to continue [Y/n]?"
read RESPONSE
case "$RESPONSE" in
	n*|N*)
	echo "Install Terminated"
	exit 0;
esac
 
#Get serial number
echo "If you have not already done so, you can get your serial number from: http://students.autodesk.com"
echo "Enter the serial number"
read SERIALNUMBER
echo ""
 
#Create a temp folder for the install files 
if [ ! -d "$HOME/mayaTempInstall" ]; then
	mkdir $HOME/$INSTALL
	echo "Creating $INSTALL folder"
	echo ""
fi
export INSTALLDIR=$HOME/$INSTALL
cd $INSTALLDIR
 
#Get Maya
wget --referer="http://trial.autodesk.com" --content-disposition $URL
 
 
 
# Install Dependencies
#I changed this a bit because for some reason alien would never install for me
#also note -y was added so you can leave the script alone and not having it snag on asking for user input
#well, the MS agreement will still stop it :(
sudo apt-get install -y alien
sudo apt-get install -y csh tcsh libaudiofile-dev libglw1-mesa elfutils
sudo apt-get install -y gamin libglw1-mesa-dev mesa-utils xfs xfstt 
sudo apt-get install -y ttf-liberation xfonts-100dpi xfonts-75dpi
sudo apt-get install -y ttf-mscorefonts-installer
sleep 3s
 
#This is in case of name change (due to new service pack or something)
FILE=Autodesk_Maya*.tgz
# Extract Maya Install Files
tar xvf $INSTALLDIR/$FILE
 
 
#prevents composite from messing up your system.... (it happened to me with 2013, I had to re-install...)
rm $INSTALLDIR/Composite*
 
#this is to free up some space. comment out this line and the wget line
#if you are doing testing that will require using the script multiple times
sudo rm $INSTALLDIR/Autodesk_Maya*
 
 
# Convert rpms to debs
for i in $INSTALLDIR/*.rpm; do
  sudo alien -cv $i;
done
sleep 2s
 
#again, space saving step.
sudo rm $INSTALLDIR/*.rpm
 
#install the debs
sudo dpkg -i $INSTALLDIR/*.deb
 
#Setup For Mental Ray.
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
 
#font issue fix
xset +fp /usr/share/fonts/X11/100dpi/
xset +fp /usr/share/fonts/X11/75dpi/
 
#fixing a few lib issues
sudo cp $INSTALLDIR/libadlmPIT* /usr/lib/libadlmPIT.so.7
sudo cp $INSTALLDIR/libadlmutil* /usr/lib/libadlmutil.so.7
 
# License Setup:
sudo echo -e 'MAYA_LICENSE=unlimited\nMAYA_LICENSE_METHOD=standalone' > /usr/autodesk/maya2014-x64/bin/License.env
#Notice the lack of sudo.
/usr/autodesk/maya2014-x64/bin/adlmreg -i S 657F1 657F1 2014.0.0.F $SERIALNUMBER /var/opt/Autodesk/Adlm/Maya2014/MayaConfig.pit
 
# symbolic links:
# Its preferred to use the libssl and libcrypto that’s included with your system... so we’ll try that first.
# We’ll use the files included by autodesk as a fallback
 
#Libssl Link
if [ -f "$LIBSSL" ]
then
	echo "$LIBSSL found. Using it."
	ln -s $LIBSSL /usr/autodesk/maya2014-x64/lib/libssl.so.10
else
	echo "$LIBSSL not found. Using Autodesk’s libssl"
	sudo ln -s /usr/autodesk/maya2014-x64/support/openssl/libssl.so.6 /usr/autodesk/maya2014-x64/lib/libssl.so.10
fi
 
#LibCrypto Link
if [ -f "$LIBCRYPTO" ]
then
	echo "$LIBCRYPTO found. Using it."
	ln -s $LIBCRYPTO /usr/autodesk/maya2014-x64/lib/libcrypto.so.10
else
	echo "$LIBCRYPTO not found. Using Autodesk’s libssl"
	sudo ln -s /usr/autodesk/maya2014-x64/support/openssl/libcrypto.so.6 /usr/autodesk/maya2014-x64/lib/libcrypto.so.10
fi
 
# libtiff
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3
sleep 2s
 
#libjpeg
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2 /usr/lib/libjpeg.so.62
 
#Everything should work now... 
echo "Installation Complete."
echo ""
echo "Start Maya Now?"
read RUNNOW
case "$RUNNOW" in
	n*|N*)
	echo "You can run maya any time by typing maya into the terminal"
	exit 0;
esac
maya
```

I navigated to the directory where the script was located in my case $ cd ~/Documents and ran **sudo bash maya_2014.sh**

after it was finished installing it asked if I wanted to run Maya and I was greeted with the following out put. 

```
/usr/autodesk/maya2014-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
```

libtiff.so.3 and its directory do exist. I'm not exactly sure where to go from here. After searching on-line its become apparent that others are having a similar issue as well. I'd really appreciate any help with the problem and or script. 

Cheers.

---

### Post by niallcd on 2013-05-30
Soooo... I tried creating a soft link to libtiff.so.3.... 

```
$ sudo ln -s /usr/lib/libtiff.so.3 /usr/lib/libtiff.so.4
```

Thus changing the out put. For the worse I think.... 

```
/usr/autodesk/maya2014-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: Error 40

```

---

### Post by Toz on 2013-05-30
> /usr/autodesk/maya2014-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

> # libtiff
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 **/usr/lib/libtiff.so.3**

As of version 11.04, ubuntu no longer, by default, uses /usr/lib as a library location. See [here]("https://wiki.ubuntu.com/MultiarchSpec") for more info on multiarch.

You could try:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/[COLOR="#FF0000"]x86_64-linux-gnu[/COLOR]/libtiff.so.3
```

Probably will have to do same with libjpeg:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2 /usr/lib/[COLOR="#FF0000"]x86_64-linux-gnu[/COLOR]/libjpeg.so.62
```

---

### Post by niallcd on 2013-05-30
Hey thanks for responding. I read the link provided and tried your code. No luck I'm afraid. 

The output: /usr/autodesk/maya2014-x64/bin/maya.bin: error while loading shared libraries: libtiff.so.3: cannot open shared object file: Error 40

I'm still looking around to see if there is a solution. When I find one I'll post it here. If we can get this working I'll be posting a guide for others to follow and trying to keep this topic active on these forums. It seems to be a frequent enough topic. 

Thanks.

---

### Post by Toz on 2013-05-30
What does the following return?
```
ls -l /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

EDIT:
And what does the following return:
```
ldd /usr/autodesk/maya2014-x64/bin/maya.bin
```

---

### Post by niallcd on 2013-05-30
Ok I just realized I could be clearer. 

So the output of 
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

Was

```
ln: failed to create symbolic link ‘/usr/lib/x86_64-linux-gnu/libtiff.so.3’: File exists
```

And the output of

```
sudo ln -s /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2 /usr/lib/x86_64-linux-gnu/libjpeg.so.62
```

Was 

```
ln: failed to create symbolic link ‘/usr/lib/x86_64-linux-gnu/libjpeg.so.62’: File exists
```

Sorry about that.

---

### Post by Toz on 2013-05-30
What do the following return:
```
ls -l /usr/lib/x86_64-linux-gnu/libtiff.so.3
```
```
ls -l /usr/lib/x86_64-linux-gnu/libjpeg.so.62
```

---

### Post by niallcd on 2013-05-30
For the output of: 

```
ls -l /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

Was:

```
lrwxrwxrwx 1 root root 42 May 30 12:46 /usr/lib/x86_64-linux-gnu/libtiff.so.3 -> /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
```

And the output of:

```
ldd /usr/autodesk/maya2014-x64/bin/maya.bin
```

Was:
	```
linux-vdso.so.1 =>  (0x00007fff7313c000)
	libMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libMaya.so (0x00007ffc7844c000)
	libawxml2.so => /usr/autodesk/maya2014-x64/bin/../lib/libawxml2.so (0x00007ffc78127000)
	libIMFbase.so => /usr/autodesk/maya2014-x64/bin/../lib/libIMFbase.so (0x00007ffc77e7f000)
	libawMarkingMenus.so => /usr/autodesk/maya2014-x64/bin/../lib/libawMarkingMenus.so (0x00007ffc77c4c000)
	libAG.so => /usr/autodesk/maya2014-x64/bin/../lib/libAG.so (0x00007ffc77639000)
	libiff.so => /usr/autodesk/maya2014-x64/bin/../lib/libiff.so (0x00007ffc77402000)
	libawGR.so => /usr/autodesk/maya2014-x64/bin/../lib/libawGR.so (0x00007ffc771f2000)
	libAppVersion.so => /usr/autodesk/maya2014-x64/bin/../lib/libAppVersion.so (0x00007ffc76ff1000)
	libFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libFoundation.so (0x00007ffc76a53000)
	libAnimEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimEngine.so (0x00007ffc767b9000)
	libCommandEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libCommandEngine.so (0x00007ffc7649c000)
	libDependEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependEngine.so (0x00007ffc75fa2000)
	libGeometryEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryEngine.so (0x00007ffc75d45000)
	libNurbsEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsEngine.so (0x00007ffc75944000)
	libImage.so => /usr/autodesk/maya2014-x64/bin/../lib/libImage.so (0x00007ffc756b5000)
	libDependCommand.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependCommand.so (0x00007ffc75487000)
	libExtensionLayer.so => /usr/autodesk/maya2014-x64/bin/../lib/libExtensionLayer.so (0x00007ffc74d4a000)
	libDataModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libDataModel.so (0x00007ffc74369000)
	libPolyEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolyEngine.so (0x00007ffc73db1000)
	lib3dGraphics.so => /usr/autodesk/maya2014-x64/bin/../lib/lib3dGraphics.so (0x00007ffc73b40000)
	libNurbs.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbs.so (0x00007ffc7379e000)
	libRenderModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderModel.so (0x00007ffc72df8000)
	libPoly.so => /usr/autodesk/maya2014-x64/bin/../lib/libPoly.so (0x00007ffc72a21000)
	libShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libShared.so (0x00007ffc71ef1000)
	libPolySlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolySlice.so (0x00007ffc71888000)
	libSharedUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libSharedUI.so (0x00007ffc70ec9000)
	libHWFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWFoundation.so (0x00007ffc70c7c000)
	libHWGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWGL.so (0x00007ffc70a0b000)
	libHWRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRender.so (0x00007ffc7079d000)
	libHWRenderMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRenderMaya.so (0x00007ffc70503000)
	libOGSRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSRender.so (0x00007ffc7006c000)
	libOGSMayaBridge.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMayaBridge.so (0x00007ffc6faa9000)
	libRenderSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderSlice.so (0x00007ffc6f542000)
	libMetaData.so => /usr/autodesk/maya2014-x64/bin/../lib/libMetaData.so (0x00007ffc6f2e1000)
	libDeformSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDeformSlice.so (0x00007ffc6edd2000)
	libModelSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libModelSlice.so (0x00007ffc6eac5000)
	libNurbsSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsSlice.so (0x00007ffc6e524000)
	libAnimSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimSlice.so (0x00007ffc6df89000)
	libKinSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libKinSlice.so (0x00007ffc6d6e7000)
	libTranslators.so => /usr/autodesk/maya2014-x64/bin/../lib/libTranslators.so (0x00007ffc6d468000)
	libBase.so => /usr/autodesk/maya2014-x64/bin/../lib/libBase.so (0x00007ffc6d130000)
	libadlmint.so.7 => /usr/autodesk/maya2014-x64/bin/../lib/libadlmint.so.7 (0x00007ffc6cb3c000)
	libQtCore.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtCore.so.4 (0x00007ffc6c639000)
	libQtGui.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtGui.so.4 (0x00007ffc6b8e9000)
	libQtSvg.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtSvg.so.4 (0x00007ffc6b689000)
	libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007ffc6b3f6000)
	libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007ffc6b197000)
	libXm.so.3 => /usr/autodesk/maya2014-x64/bin/../lib/libXm.so.3 (0x00007ffc6ae08000)
	libXp.so.6 => /usr/lib/x86_64-linux-gnu/libXp.so.6 (0x00007ffc6abff000)
	libXmu.so.6 => /usr/lib/x86_64-linux-gnu/libXmu.so.6 (0x00007ffc6a9e6000)
	libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007ffc6a7d3000)
	libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007ffc6a56d000)
	libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007ffc6a35e000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007ffc6a14b000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007ffc69e11000)
	libimf.so => /usr/autodesk/maya2014-x64/bin/../lib/libimf.so (0x00007ffc69a45000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007ffc6973f000)
	libtbb.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbb.so.2 (0x00007ffc695f2000)
	libtbbmalloc.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbbmalloc.so.2 (0x00007ffc694ae000)
	libsvml.so => /usr/autodesk/maya2014-x64/bin/../lib/libsvml.so (0x00007ffc68d33000)
	libiomp5.so => /usr/autodesk/maya2014-x64/bin/../lib/libiomp5.so (0x00007ffc68a45000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007ffc68742000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007ffc6852b000)
	libintlc.so.5 => /usr/autodesk/maya2014-x64/bin/../lib/libintlc.so.5 (0x00007ffc683dc000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007ffc681bf000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007ffc67df6000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007ffc67bf2000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007ffc679da000)
	libawDebugTools.so => /usr/autodesk/maya2014-x64/bin/../lib/libawDebugTools.so (0x00007ffc677d6000)
	libQtOpenGL.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtOpenGL.so.4 (0x00007ffc674c9000)
	libsynHub.so => /usr/autodesk/maya2014-x64/bin/../lib/libsynHub.so (0x00007ffc66f18000)
	libpython2.7.so.1.0 => /usr/autodesk/maya2014-x64/bin/../lib/libpython2.7.so.1.0 (0x00007ffc66b4c000)
	libquicktime.so.0 => /usr/autodesk/maya2014-x64/bin/../lib/libquicktime.so.0 (0x00007ffc6688d000)
	libQtWebKit.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtWebKit.so.4 (0x00007ffc64c92000)
	libQtNetwork.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtNetwork.so.4 (0x00007ffc64931000)
	libQtScript.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtScript.so.4 (0x00007ffc64467000)
	libtiff.so.3 => not found
	libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007ffc64263000)
	libPtex.so => /usr/autodesk/maya2014-x64/bin/../lib/libPtex.so (0x00007ffc63fcb000)
	libawCacheShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libawCacheShared.so (0x00007ffc63dab000)
	libQtXml.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtXml.so.4 (0x00007ffc63b61000)
	libfbxassetscore2.so => /usr/autodesk/maya2014-x64/bin/../lib/libfbxassetscore2.so (0x00007ffc637db000)
	libopenal.so.1 => /usr/autodesk/maya2014-x64/bin/../lib/libopenal.so.1 (0x00007ffc6358b000)
	libfam.so.0 => /usr/lib/libfam.so.0 (0x00007ffc63383000)
	libGeometryDefn.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryDefn.so (0x00007ffc63138000)
	libGeometryAlg.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryAlg.so (0x00007ffc62e02000)
	libTesselation.so => /usr/autodesk/maya2014-x64/bin/../lib/libTesselation.so (0x00007ffc62b32000)
	libawnSolver.so => /usr/autodesk/maya2014-x64/bin/../lib/libawnSolver.so (0x00007ffc62761000)
	libSubdivEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivEngine.so (0x00007ffc624b0000)
	libSubdivGeom.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivGeom.so (0x00007ffc62243000)
	libSubdiv.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdiv.so (0x00007ffc61e8d000)
	libDynSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDynSlice.so (0x00007ffc6151c000)
	libadp_core-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_core-4_0.so (0x00007ffc61193000)
	libadp_data-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_data-4_0.so (0x00007ffc60f24000)
	libadp_service_opczip-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_service_opczip-4_0.so (0x00007ffc60d09000)
	libadp_toolkit-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_toolkit-4_0.so (0x00007ffc60870000)
	libMgMdfModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfModel.so (0x00007ffc605fe000)
	libMgMdfParser.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfParser.so (0x00007ffc60320000)
	libOGSAtilIntegration-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSAtilIntegration-4_0.so (0x00007ffc5f852000)
	libOGSDevices-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDevices-4_0.so (0x00007ffc5f0b5000)
	libOGSGraphics-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSGraphics-4_0.so (0x00007ffc5e6bc000)
	libOGSObjects-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSObjects-4_0.so (0x00007ffc5e2cc000)
	libOGSMgStylization-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMgStylization-4_0.so (0x00007ffc5df46000)
	libOGSDeviceOGL-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDeviceOGL-4_0.so (0x00007ffc5dc93000)
	libweightXML.so => /usr/autodesk/maya2014-x64/bin/../lib/libweightXML.so (0x00007ffc5da8e000)
	libManips.so => /usr/autodesk/maya2014-x64/bin/../lib/libManips.so (0x00007ffc5d595000)
	libImageUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libImageUI.so (0x00007ffc5d167000)
	libModifiers.so => /usr/autodesk/maya2014-x64/bin/../lib/libModifiers.so (0x00007ffc5cdd5000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007ffc5cbcb000)
	libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007ffc5c9c6000)
	libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007ffc5c7c3000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007ffc5c4c7000)
	/lib64/ld-linux-x86-64.so.2 (0x00007ffc7864f000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007ffc5c2a0000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007ffc5c003000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007ffc5bdb4000)
	libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007ffc5bbac000)
	libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007ffc5b98f000)
	libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007ffc5b785000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007ffc5b54b000)
	libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007ffc5b324000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007ffc5b121000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007ffc5af1a000)
	libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007ffc5ad18000)
	libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007ffc5ab01000)
	libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007ffc5a8fb000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007ffc5a6dd000)
	libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007ffc5a4d7000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007ffc5a2cb000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007ffc5a0c7000)
	libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007ffc59ec3000)
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007ffc59b69000)
	libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007ffc5995c000)
	libgstinterfaces-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstinterfaces-0.10.so.0 (0x00007ffc5974a000)
	libgstpbutils-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstpbutils-0.10.so.0 (0x00007ffc59526000)
	libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007ffc59309000)
	libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007ffc590b5000)
	libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007ffc58dcf000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007ffc58bca000)
	libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007ffc58867000)
	libxerces-c.so.27 => /usr/autodesk/maya2014-x64/bin/../lib/libxerces-c.so.27 (0x00007ffc58250000)
	libOGSArchive-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSArchive-4_0.so (0x00007ffc5801f000)
	libNsArchive10.so => /usr/autodesk/maya2014-x64/bin/../lib/libNsArchive10.so (0x00007ffc57e19000)
	libssl.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libssl.so.10 (0x00007ffc57bcb000)
	libcrypto.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libcrypto.so.10 (0x00007ffc57877000)
	libCg.so => /usr/autodesk/maya2014-x64/bin/../lib/libCg.so (0x00007ffc5677d000)
	libCgGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libCgGL.so (0x00007ffc565fb000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007ffc563bb000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007ffc561b2000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007ffc55f89000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007ffc55d82000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007ffc55b63000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007ffc55949000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007ffc556ca000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007ffc554a8000)
	libziparch.so => /usr/autodesk/maya2014-x64/bin/../lib/libziparch.so (0x00007ffc551e0000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007ffc54fa2000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007ffc54cd3000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007ffc54acf000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007ffc548a6000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007ffc5469d000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007ffc54499000)

```

Thanks for all the help.

---

### Post by niallcd on 2013-05-30
Additionally the output of:

```
ls -l /usr/lib/x86_64-linux-gnu/libjpeg.so.62
```

Was:

```
lrwxrwxrwx 1 root root 42 May 30 12:46 /usr/lib/x86_64-linux-gnu/libjpeg.so.62 -> /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2
```

---

### Post by Toz on 2013-05-30
Can you, one more time:
```
ls -l /usr/lib/x86_64-linux-gnu/libtiff*
```
...lets see them all.

---

### Post by niallcd on 2013-05-30
So here's the output of 
```
ls -l /usr/lib/x86_64-linux-gnu/libtiff*
```

Output:
```
lrwxrwxrwx 1 root root     42 May 30 12:46 /usr/lib/x86_64-linux-gnu/libtiff.so.3 -> /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
lrwxrwxrwx 1 root root     16 May 30 08:44 /usr/lib/x86_64-linux-gnu/libtiff.so.5 -> libtiff.so.5.1.0
-rw-r--r-- 1 root root 462560 Nov 15  2012 /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0

```

---

### Post by Toz on 2013-05-30
Thats interesting, there is no /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 in that directory to link to. First try removing that link:
```
sudo rm /usr/lib/x86_64-linux-gnu/libtiff.so.3
```
...then based on the code, try this:
```
sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0 /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

Post back again:
```
ls -l /usr/lib/x86_64-linux-gnu/libtiff*
```
...and:
```
ldd /usr/autodesk/maya2014-x64/bin/maya.bin
```
...and try running the program again.

---

### Post by niallcd on 2013-05-30
That seemed to fix it! Though I'm not sure what you did.

Output of:
```
sudo rm /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

Was:
```
lrwxrwxrwx 1 root root     42 May 30 13:40 /usr/lib/x86_64-linux-gnu/libtiff.so.3 -> /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0
lrwxrwxrwx 1 root root     16 May 30 08:44 /usr/lib/x86_64-linux-gnu/libtiff.so.5 -> libtiff.so.5.1.0
-rw-r--r-- 1 root root 462560 Nov 15  2012 /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0
```

And the Output of:
```
ldd /usr/autodesk/maya2014-x64/bin/maya.bin
```

Was:
```
	libawMarkingMenus.so => /usr/autodesk/maya2014-x64/bin/../lib/libawMarkingMenus.so (0x00007f2a5a809000)
	libAG.so => /usr/autodesk/maya2014-x64/bin/../lib/libAG.so (0x00007f2a5a1f6000)
	libiff.so => /usr/autodesk/maya2014-x64/bin/../lib/libiff.so (0x00007f2a59fbf000)
	libawGR.so => /usr/autodesk/maya2014-x64/bin/../lib/libawGR.so (0x00007f2a59daf000)
	libAppVersion.so => /usr/autodesk/maya2014-x64/bin/../lib/libAppVersion.so (0x00007f2a59bae000)
	libFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libFoundation.so (0x00007f2a59610000)
	libAnimEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimEngine.so (0x00007f2a59376000)
	libCommandEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libCommandEngine.so (0x00007f2a59059000)
	libDependEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependEngine.so (0x00007f2a58b5f000)
	libGeometryEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryEngine.so (0x00007f2a58902000)
	libNurbsEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsEngine.so (0x00007f2a58501000)
	libImage.so => /usr/autodesk/maya2014-x64/bin/../lib/libImage.so (0x00007f2a58272000)
	libDependCommand.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependCommand.so (0x00007f2a58044000)
	libExtensionLayer.so => /usr/autodesk/maya2014-x64/bin/../lib/libExtensionLayer.so (0x00007f2a57907000)
	libDataModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libDataModel.so (0x00007f2a56f26000)
	libPolyEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolyEngine.so (0x00007f2a5696e000)
	lib3dGraphics.so => /usr/autodesk/maya2014-x64/bin/../lib/lib3dGraphics.so (0x00007f2a566fd000)
	libNurbs.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbs.so (0x00007f2a5635b000)
	libRenderModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderModel.so (0x00007f2a559b5000)
	libPoly.so => /usr/autodesk/maya2014-x64/bin/../lib/libPoly.so (0x00007f2a555de000)
	libShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libShared.so (0x00007f2a54aae000)
	libPolySlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolySlice.so (0x00007f2a54445000)
	libSharedUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libSharedUI.so (0x00007f2a53a86000)
	libHWFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWFoundation.so (0x00007f2a53839000)
	libHWGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWGL.so (0x00007f2a535c8000)
	libHWRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRender.so (0x00007f2a5335a000)
	libHWRenderMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRenderMaya.so (0x00007f2a530c0000)
	libOGSRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSRender.so (0x00007f2a52c29000)
	libOGSMayaBridge.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMayaBridge.so (0x00007f2a52666000)
	libRenderSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderSlice.so (0x00007f2a520ff000)
	libMetaData.so => /usr/autodesk/maya2014-x64/bin/../lib/libMetaData.so (0x00007f2a51e9e000)
	libDeformSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDeformSlice.so (0x00007f2a5198f000)
	libModelSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libModelSlice.so (0x00007f2a51682000)
	libNurbsSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsSlice.so (0x00007f2a510e1000)
	libAnimSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimSlice.so (0x00007f2a50b46000)
	libKinSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libKinSlice.so (0x00007f2a502a4000)
	libTranslators.so => /usr/autodesk/maya2014-x64/bin/../lib/libTranslators.so (0x00007f2a50025000)
	libBase.so => /usr/autodesk/maya2014-x64/bin/../lib/libBase.so (0x00007f2a4fced000)
	libadlmint.so.7 => /usr/autodesk/maya2014-x64/bin/../lib/libadlmint.so.7 (0x00007f2a4f6f9000)
	libQtCore.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtCore.so.4 (0x00007f2a4f1f6000)
	libQtGui.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtGui.so.4 (0x00007f2a4e4a6000)
	libQtSvg.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtSvg.so.4 (0x00007f2a4e246000)
	libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007f2a4dfb3000)
	libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007f2a4dd54000)
	libXm.so.3 => /usr/autodesk/maya2014-x64/bin/../lib/libXm.so.3 (0x00007f2a4d9c5000)
	libXp.so.6 => /usr/lib/x86_64-linux-gnu/libXp.so.6 (0x00007f2a4d7bc000)
	libXmu.so.6 => /usr/lib/x86_64-linux-gnu/libXmu.so.6 (0x00007f2a4d5a3000)
	libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007f2a4d390000)
	libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007f2a4d12a000)
	libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007f2a4cf1b000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007f2a4cd08000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007f2a4c9ce000)
	libimf.so => /usr/autodesk/maya2014-x64/bin/../lib/libimf.so (0x00007f2a4c602000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007f2a4c2fc000)
	libtbb.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbb.so.2 (0x00007f2a4c1af000)
	libtbbmalloc.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbbmalloc.so.2 (0x00007f2a4c06b000)
	libsvml.so => /usr/autodesk/maya2014-x64/bin/../lib/libsvml.so (0x00007f2a4b8f0000)
	libiomp5.so => /usr/autodesk/maya2014-x64/bin/../lib/libiomp5.so (0x00007f2a4b602000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007f2a4b2ff000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007f2a4b0e8000)
	libintlc.so.5 => /usr/autodesk/maya2014-x64/bin/../lib/libintlc.so.5 (0x00007f2a4af99000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007f2a4ad7c000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007f2a4a9b3000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007f2a4a7af000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f2a4a597000)
	libawDebugTools.so => /usr/autodesk/maya2014-x64/bin/../lib/libawDebugTools.so (0x00007f2a4a393000)
	libQtOpenGL.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtOpenGL.so.4 (0x00007f2a4a086000)
	libsynHub.so => /usr/autodesk/maya2014-x64/bin/../lib/libsynHub.so (0x00007f2a49ad5000)
	libpython2.7.so.1.0 => /usr/autodesk/maya2014-x64/bin/../lib/libpython2.7.so.1.0 (0x00007f2a49709000)
	libquicktime.so.0 => /usr/autodesk/maya2014-x64/bin/../lib/libquicktime.so.0 (0x00007f2a4944a000)
	libQtWebKit.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtWebKit.so.4 (0x00007f2a4784f000)
	libQtNetwork.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtNetwork.so.4 (0x00007f2a474ee000)
	libQtScript.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtScript.so.4 (0x00007f2a47024000)
	libtiff.so.3 => /usr/lib/x86_64-linux-gnu/libtiff.so.3 (0x00007f2a46db2000)
	libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007f2a46baf000)
	libPtex.so => /usr/autodesk/maya2014-x64/bin/../lib/libPtex.so (0x00007f2a46917000)
	libawCacheShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libawCacheShared.so (0x00007f2a466f7000)
	libQtXml.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtXml.so.4 (0x00007f2a464ad000)
	libfbxassetscore2.so => /usr/autodesk/maya2014-x64/bin/../lib/libfbxassetscore2.so (0x00007f2a46127000)
	libopenal.so.1 => /usr/autodesk/maya2014-x64/bin/../lib/libopenal.so.1 (0x00007f2a45ed7000)
	libfam.so.0 => /usr/lib/libfam.so.0 (0x00007f2a45ccf000)
	libGeometryDefn.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryDefn.so (0x00007f2a45a84000)
	libGeometryAlg.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryAlg.so (0x00007f2a4574e000)
	libTesselation.so => /usr/autodesk/maya2014-x64/bin/../lib/libTesselation.so (0x00007f2a4547e000)
	libawnSolver.so => /usr/autodesk/maya2014-x64/bin/../lib/libawnSolver.so (0x00007f2a450ad000)
	libSubdivEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivEngine.so (0x00007f2a44dfc000)
	libSubdivGeom.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivGeom.so (0x00007f2a44b8f000)
	libSubdiv.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdiv.so (0x00007f2a447d9000)
	libDynSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDynSlice.so (0x00007f2a43e68000)
	libadp_core-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_core-4_0.so (0x00007f2a43adf000)
	libadp_data-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_data-4_0.so (0x00007f2a43870000)
	libadp_service_opczip-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_service_opczip-4_0.so (0x00007f2a43655000)
	libadp_toolkit-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_toolkit-4_0.so (0x00007f2a431bc000)
	libMgMdfModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfModel.so (0x00007f2a42f4a000)
	libMgMdfParser.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfParser.so (0x00007f2a42c6c000)
	libOGSAtilIntegration-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSAtilIntegration-4_0.so (0x00007f2a4219e000)
	libOGSDevices-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDevices-4_0.so (0x00007f2a41a01000)
	libOGSGraphics-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSGraphics-4_0.so (0x00007f2a41008000)
	libOGSObjects-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSObjects-4_0.so (0x00007f2a40c18000)
	libOGSMgStylization-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMgStylization-4_0.so (0x00007f2a40892000)
	libOGSDeviceOGL-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDeviceOGL-4_0.so (0x00007f2a405df000)
	libweightXML.so => /usr/autodesk/maya2014-x64/bin/../lib/libweightXML.so (0x00007f2a403da000)
	libManips.so => /usr/autodesk/maya2014-x64/bin/../lib/libManips.so (0x00007f2a3fee1000)
	libImageUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libImageUI.so (0x00007f2a3fab3000)
	libModifiers.so => /usr/autodesk/maya2014-x64/bin/../lib/libModifiers.so (0x00007f2a3f721000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f2a3f517000)
	libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007f2a3f312000)
	libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007f2a3f10f000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007f2a3ee13000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f2a5b20c000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007f2a3ebec000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007f2a3e94f000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007f2a3e700000)
	libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007f2a3e4f8000)
	libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007f2a3e2db000)
	libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007f2a3e0d1000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007f2a3de97000)
	libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007f2a3dc70000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007f2a3da6d000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007f2a3d866000)
	libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007f2a3d664000)
	libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007f2a3d44d000)
	libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007f2a3d247000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007f2a3d029000)
	libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007f2a3ce23000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007f2a3cc17000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007f2a3ca13000)
	libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007f2a3c80f000)
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007f2a3c4b5000)
	libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007f2a3c2a8000)
	libgstinterfaces-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstinterfaces-0.10.so.0 (0x00007f2a3c096000)
	libgstpbutils-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstpbutils-0.10.so.0 (0x00007f2a3be72000)
	libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007f2a3bc55000)
	libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007f2a3ba01000)
	libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007f2a3b71b000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007f2a3b516000)
	libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007f2a3b1b3000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007f2a3af90000)
	libjbig.so.0 => /usr/lib/x86_64-linux-gnu/libjbig.so.0 (0x00007f2a3ad82000)
	libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007f2a3ab31000)
	libxerces-c.so.27 => /usr/autodesk/maya2014-x64/bin/../lib/libxerces-c.so.27 (0x00007f2a3a51a000)
	libOGSArchive-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSArchive-4_0.so (0x00007f2a3a2e9000)
	libNsArchive10.so => /usr/autodesk/maya2014-x64/bin/../lib/libNsArchive10.so (0x00007f2a3a0e3000)
	libssl.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libssl.so.10 (0x00007f2a39e95000)
	libcrypto.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libcrypto.so.10 (0x00007f2a39b41000)
	libCg.so => /usr/autodesk/maya2014-x64/bin/../lib/libCg.so (0x00007f2a38a47000)
	libCgGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libCgGL.so (0x00007f2a388c5000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007f2a38685000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007f2a3847c000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007f2a38253000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007f2a3804c000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007f2a37e2d000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007f2a37c13000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007f2a37994000)
	libziparch.so => /usr/autodesk/maya2014-x64/bin/../lib/libziparch.so (0x00007f2a376cc000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007f2a3748e000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f2a371c0000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f2a36fbb000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f2a36d92000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007f2a36b89000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007f2a36985000)
ncd@3d:~$ clear

ncd@3d:~$ ldd /usr/autodesk/maya2014-x64/bin/maya.bin
	linux-vdso.so.1 =>  (0x00007fff765fe000)
	libMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libMaya.so (0x00007fb2952e8000)
	libawxml2.so => /usr/autodesk/maya2014-x64/bin/../lib/libawxml2.so (0x00007fb294fc3000)
	libIMFbase.so => /usr/autodesk/maya2014-x64/bin/../lib/libIMFbase.so (0x00007fb294d1b000)
	libawMarkingMenus.so => /usr/autodesk/maya2014-x64/bin/../lib/libawMarkingMenus.so (0x00007fb294ae8000)
	libAG.so => /usr/autodesk/maya2014-x64/bin/../lib/libAG.so (0x00007fb2944d5000)
	libiff.so => /usr/autodesk/maya2014-x64/bin/../lib/libiff.so (0x00007fb29429e000)
	libawGR.so => /usr/autodesk/maya2014-x64/bin/../lib/libawGR.so (0x00007fb29408e000)
	libAppVersion.so => /usr/autodesk/maya2014-x64/bin/../lib/libAppVersion.so (0x00007fb293e8d000)
	libFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libFoundation.so (0x00007fb2938ef000)
	libAnimEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimEngine.so (0x00007fb293655000)
	libCommandEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libCommandEngine.so (0x00007fb293338000)
	libDependEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependEngine.so (0x00007fb292e3e000)
	libGeometryEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryEngine.so (0x00007fb292be1000)
	libNurbsEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsEngine.so (0x00007fb2927e0000)
	libImage.so => /usr/autodesk/maya2014-x64/bin/../lib/libImage.so (0x00007fb292551000)
	libDependCommand.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependCommand.so (0x00007fb292323000)
	libExtensionLayer.so => /usr/autodesk/maya2014-x64/bin/../lib/libExtensionLayer.so (0x00007fb291be6000)
	libDataModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libDataModel.so (0x00007fb291205000)
	libPolyEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolyEngine.so (0x00007fb290c4d000)
	lib3dGraphics.so => /usr/autodesk/maya2014-x64/bin/../lib/lib3dGraphics.so (0x00007fb2909dc000)
	libNurbs.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbs.so (0x00007fb29063a000)
	libRenderModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderModel.so (0x00007fb28fc94000)
	libPoly.so => /usr/autodesk/maya2014-x64/bin/../lib/libPoly.so (0x00007fb28f8bd000)
	libShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libShared.so (0x00007fb28ed8d000)
	libPolySlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolySlice.so (0x00007fb28e724000)
	libSharedUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libSharedUI.so (0x00007fb28dd65000)
	libHWFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWFoundation.so (0x00007fb28db18000)
	libHWGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWGL.so (0x00007fb28d8a7000)
	libHWRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRender.so (0x00007fb28d639000)
	libHWRenderMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRenderMaya.so (0x00007fb28d39f000)
	libOGSRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSRender.so (0x00007fb28cf08000)
	libOGSMayaBridge.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMayaBridge.so (0x00007fb28c945000)
	libRenderSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderSlice.so (0x00007fb28c3de000)
	libMetaData.so => /usr/autodesk/maya2014-x64/bin/../lib/libMetaData.so (0x00007fb28c17d000)
	libDeformSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDeformSlice.so (0x00007fb28bc6e000)
	libModelSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libModelSlice.so (0x00007fb28b961000)
	libNurbsSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsSlice.so (0x00007fb28b3c0000)
	libAnimSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimSlice.so (0x00007fb28ae25000)
	libKinSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libKinSlice.so (0x00007fb28a583000)
	libTranslators.so => /usr/autodesk/maya2014-x64/bin/../lib/libTranslators.so (0x00007fb28a304000)
	libBase.so => /usr/autodesk/maya2014-x64/bin/../lib/libBase.so (0x00007fb289fcc000)
	libadlmint.so.7 => /usr/autodesk/maya2014-x64/bin/../lib/libadlmint.so.7 (0x00007fb2899d8000)
	libQtCore.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtCore.so.4 (0x00007fb2894d5000)
	libQtGui.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtGui.so.4 (0x00007fb288785000)
	libQtSvg.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtSvg.so.4 (0x00007fb288525000)
	libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007fb288292000)
	libGL.so.1 => /usr/lib/x86_64-linux-gnu/mesa/libGL.so.1 (0x00007fb288033000)
	libXm.so.3 => /usr/autodesk/maya2014-x64/bin/../lib/libXm.so.3 (0x00007fb287ca4000)
	libXp.so.6 => /usr/lib/x86_64-linux-gnu/libXp.so.6 (0x00007fb287a9b000)
	libXmu.so.6 => /usr/lib/x86_64-linux-gnu/libXmu.so.6 (0x00007fb287882000)
	libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007fb28766f000)
	libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007fb287409000)
	libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007fb2871fa000)
	libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fb286fe7000)
	libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fb286cad000)
	libimf.so => /usr/autodesk/maya2014-x64/bin/../lib/libimf.so (0x00007fb2868e1000)
	libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fb2865db000)
	libtbb.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbb.so.2 (0x00007fb28648e000)
	libtbbmalloc.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbbmalloc.so.2 (0x00007fb28634a000)
	libsvml.so => /usr/autodesk/maya2014-x64/bin/../lib/libsvml.so (0x00007fb285bcf000)
	libiomp5.so => /usr/autodesk/maya2014-x64/bin/../lib/libiomp5.so (0x00007fb2858e1000)
	libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fb2855de000)
	libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fb2853c7000)
	libintlc.so.5 => /usr/autodesk/maya2014-x64/bin/../lib/libintlc.so.5 (0x00007fb285278000)
	libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fb28505b000)
	libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fb284c92000)
	libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fb284a8e000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fb284876000)
	libawDebugTools.so => /usr/autodesk/maya2014-x64/bin/../lib/libawDebugTools.so (0x00007fb284672000)
	libQtOpenGL.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtOpenGL.so.4 (0x00007fb284365000)
	libsynHub.so => /usr/autodesk/maya2014-x64/bin/../lib/libsynHub.so (0x00007fb283db4000)
	libpython2.7.so.1.0 => /usr/autodesk/maya2014-x64/bin/../lib/libpython2.7.so.1.0 (0x00007fb2839e8000)
	libquicktime.so.0 => /usr/autodesk/maya2014-x64/bin/../lib/libquicktime.so.0 (0x00007fb283729000)
	libQtWebKit.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtWebKit.so.4 (0x00007fb281b2e000)
	libQtNetwork.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtNetwork.so.4 (0x00007fb2817cd000)
	libQtScript.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtScript.so.4 (0x00007fb281303000)
	libtiff.so.3 => /usr/lib/x86_64-linux-gnu/libtiff.so.3 (0x00007fb281091000)
	libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007fb280e8e000)
	libPtex.so => /usr/autodesk/maya2014-x64/bin/../lib/libPtex.so (0x00007fb280bf6000)
	libawCacheShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libawCacheShared.so (0x00007fb2809d6000)
	libQtXml.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtXml.so.4 (0x00007fb28078c000)
	libfbxassetscore2.so => /usr/autodesk/maya2014-x64/bin/../lib/libfbxassetscore2.so (0x00007fb280406000)
	libopenal.so.1 => /usr/autodesk/maya2014-x64/bin/../lib/libopenal.so.1 (0x00007fb2801b6000)
	libfam.so.0 => /usr/lib/libfam.so.0 (0x00007fb27ffae000)
	libGeometryDefn.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryDefn.so (0x00007fb27fd63000)
	libGeometryAlg.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryAlg.so (0x00007fb27fa2d000)
	libTesselation.so => /usr/autodesk/maya2014-x64/bin/../lib/libTesselation.so (0x00007fb27f75d000)
	libawnSolver.so => /usr/autodesk/maya2014-x64/bin/../lib/libawnSolver.so (0x00007fb27f38c000)
	libSubdivEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivEngine.so (0x00007fb27f0db000)
	libSubdivGeom.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivGeom.so (0x00007fb27ee6e000)
	libSubdiv.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdiv.so (0x00007fb27eab8000)
	libDynSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDynSlice.so (0x00007fb27e147000)
	libadp_core-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_core-4_0.so (0x00007fb27ddbe000)
	libadp_data-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_data-4_0.so (0x00007fb27db4f000)
	libadp_service_opczip-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_service_opczip-4_0.so (0x00007fb27d934000)
	libadp_toolkit-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_toolkit-4_0.so (0x00007fb27d49b000)
	libMgMdfModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfModel.so (0x00007fb27d229000)
	libMgMdfParser.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfParser.so (0x00007fb27cf4b000)
	libOGSAtilIntegration-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSAtilIntegration-4_0.so (0x00007fb27c47d000)
	libOGSDevices-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDevices-4_0.so (0x00007fb27bce0000)
	libOGSGraphics-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSGraphics-4_0.so (0x00007fb27b2e7000)
	libOGSObjects-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSObjects-4_0.so (0x00007fb27aef7000)
	libOGSMgStylization-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMgStylization-4_0.so (0x00007fb27ab71000)
	libOGSDeviceOGL-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDeviceOGL-4_0.so (0x00007fb27a8be000)
	libweightXML.so => /usr/autodesk/maya2014-x64/bin/../lib/libweightXML.so (0x00007fb27a6b9000)
	libManips.so => /usr/autodesk/maya2014-x64/bin/../lib/libManips.so (0x00007fb27a1c0000)
	libImageUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libImageUI.so (0x00007fb279d92000)
	libModifiers.so => /usr/autodesk/maya2014-x64/bin/../lib/libModifiers.so (0x00007fb279a00000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fb2797f6000)
	libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007fb2795f1000)
	libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007fb2793ee000)
	libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fb2790f2000)
	/lib64/ld-linux-x86-64.so.2 (0x00007fb2954eb000)
	libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fb278ecb000)
	libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fb278c2e000)
	libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fb2789df000)
	libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007fb2787d7000)
	libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007fb2785ba000)
	libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007fb2783b0000)
	libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fb278176000)
	libglapi.so.0 => /usr/lib/x86_64-linux-gnu/libglapi.so.0 (0x00007fb277f4f000)
	libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fb277d4c000)
	libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fb277b45000)
	libX11-xcb.so.1 => /usr/lib/x86_64-linux-gnu/libX11-xcb.so.1 (0x00007fb277943000)
	libxcb-glx.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-glx.so.0 (0x00007fb27772c000)
	libxcb-dri2.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-dri2.so.0 (0x00007fb277526000)
	libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fb277308000)
	libXxf86vm.so.1 => /usr/lib/x86_64-linux-gnu/libXxf86vm.so.1 (0x00007fb277102000)
	libdrm.so.2 => /usr/lib/x86_64-linux-gnu/libdrm.so.2 (0x00007fb276ef6000)
	libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fb276cf2000)
	libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007fb276aee000)
	libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007fb276794000)
	libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007fb276587000)
	libgstinterfaces-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstinterfaces-0.10.so.0 (0x00007fb276375000)
	libgstpbutils-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstpbutils-0.10.so.0 (0x00007fb276151000)
	libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007fb275f34000)
	libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007fb275ce0000)
	libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007fb2759fa000)
	libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fb2757f5000)
	libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007fb275492000)
	liblzma.so.5 => /lib/x86_64-linux-gnu/liblzma.so.5 (0x00007fb27526f000)
	libjbig.so.0 => /usr/lib/x86_64-linux-gnu/libjbig.so.0 (0x00007fb275061000)
	libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007fb274e10000)
	libxerces-c.so.27 => /usr/autodesk/maya2014-x64/bin/../lib/libxerces-c.so.27 (0x00007fb2747f9000)
	libOGSArchive-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSArchive-4_0.so (0x00007fb2745c8000)
	libNsArchive10.so => /usr/autodesk/maya2014-x64/bin/../lib/libNsArchive10.so (0x00007fb2743c2000)
	libssl.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libssl.so.10 (0x00007fb274174000)
	libcrypto.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libcrypto.so.10 (0x00007fb273e20000)
	libCg.so => /usr/autodesk/maya2014-x64/bin/../lib/libCg.so (0x00007fb272d26000)
	libCgGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libCgGL.so (0x00007fb272ba4000)
	libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fb272964000)
	libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fb27275b000)
	libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fb272532000)
	libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fb27232b000)
	libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fb27210c000)
	libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fb271ef2000)
	liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fb271c73000)
	libziparch.so => /usr/autodesk/maya2014-x64/bin/../lib/libziparch.so (0x00007fb2719ab000)
	libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fb27176d000)
	libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fb27149f000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fb27129a000)
	libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fb271071000)
	libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fb270e68000)
	libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fb270c64000)

```

I had a license error but thats my fault and will try fixing that now. Really all of your help is really appreciated. Thank you so much. I'll report back on if it works once I give it the right license.

---

### Post by Toz on 2013-05-30
> That seemed to fix it! Though I'm not sure what you did.
It would appear as though the script is linking to a specific library version of libtiff that isn't guaranteed to be installed on a system. Plus, its being linked into the wrong directory for Ubuntu. I simply fixed that (linked to the correctly installed library in the right diretory).

---

### Post by niallcd on 2013-05-30
Amazing! its works. I'm going to edit the script to make the appropriate changes. Would you take a look and see if the changes I made are correct so others can use it in the future?

---

### Post by niallcd on 2013-05-30
Hey there. So I made the change by replacing 
        **sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4 /usr/lib/libtiff.so.3**

with: **sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0 /usr/lib/x86_64-linux-gnu/libtiff.so.3**

```
#### Lets run a few checks to make sure things work as expected.
#Make sure we’re running with root permissions.
if [ `whoami` != root ]; then
   echo Please run this script using sudo
   echo Just type “sudo !!”
   exit
fi
#Check for 64-bit arch
if [uname -m != x86_64]; then
   echo Maya will only run on 64-bit linux.
   echo Please install the 64-bit ubuntu and try again.
   exit
fi
 
#Setup a few vars
export MAYAINSTALL='mayaTempInstall'
export RPM_INSTALL_PREFIX=/usr
export LD_LIBRARY_PATH=/opt/Autodesk/Adlm/R5/lib64/
LIBCRYPTO="/usr/lib/x86_64-linux-gnu/libcrypto.so.0.9.8"
LIBSSL="/usr/lib/x86_64-linux-gnu/libssl.so.0.9.8"
MAYAURL="http://download.autodesk.com/us/maya/service_packs/Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz"
 
#Install Message
echo "You’re about to download and install Autodesk Maya 2013"
echo ""
echo "Do you wish to continue [Y/n]?"
read RESPONSE
case "$RESPONSE" in
	n*|N*)
	echo "Install Terminated"
	exit 0;
esac
 
#Get serial number
echo "If you have not already done so, you can get your serial number from: http://students.autodesk.com"
echo "Enter the serial number"
read SERIALNUMBER
echo ""
 
#Create a temp folder for the install files
if [ ! -d "$HOME/mayaInstaller" ]; then
	mkdir $HOME/$MAYAINSTALL
	echo "Creating $MAYAINSTALL folder"
	echo ""
fi
export INSTALLDIR=$HOME/MAYAINSTALL
cd $INSTALLDIR
 
#Get Maya
wget --referer="http://trial.autodesk.com" --content-disposition $MAYAURL
 
# Install Dependencies
sudo apt-get install csh tcsh libaudiofile-dev libglw1-mesa elfutils gamin libglw1-mesa-dev mesa-utils xfs xfstt ttf-liberation ttf-mscorefonts-installer xfonts-100dpi xfonts-75dpi alien
sleep 3s
 
#This is in case of name change (due to new service pack or something)
MAYAFILE=Autodesk*.tgz
# Extract Maya Install Files
tar xvf $INSTALLDIR/$MAYAFILE
# Convert rpms to debs
sudo for i in $INSTALLDIR/*.rpm; do sudo alien -cv $i; done
sleep 2s
#install the debs
sudo dpkg -i $INSTALLDIR/*.deb
 
#Setup For Mental Ray.
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
 
# License Setup:
sudo echo -e 'MAYA_LICENSE=unlimited\nMAYA_LICENSE_METHOD=standalone' > /usr/autodesk/maya2013-x64/bin/License.env
#Notice the lack of sudo.
/usr/autodesk/maya2013-x64/bin/adlmreg -i S 657E1 657E1 2013.0.0.F $SERIALNUMBER /var/opt/Autodesk/Adlm/Maya2013/MayaConfig.pit
 
# symbolic links:
# Its preferred to use the libssl and libcrypto that’s included with your system... so we’ll try that first.
# We’ll use the files included by autodesk as a fallback
 
#Libssl Link
if [ -f "$LIBSSL" ]
then
	echo "$LIBSSL found. Using it."
	ln -s $LIBSSL /usr/autodesk/maya2013-x64/lib/libssl.so.6
else
	echo "$LIBSSL not found. Using Autodesk’s libssl"
	sudo ln -s /usr/autodesk/maya2013-x64/support/openssl/libssl.so.6 /usr/autodesk/maya2013-x64/lib/libssl.so.6
fi
 
#LibCrypto Link
if [ -f "$LIBCRYPTO" ]
then
	echo "$LIBCRYPTO found. Using it."
	ln -s $LIBCRYPTO /usr/autodesk/maya2013-x64/lib/libcrypto.so.6
else
	echo "$LIBCRYPTO not found. Using Autodesk’s libssl"
	sudo ln -s /usr/autodesk/maya2013-x64/support/openssl/libcrypto.so.6 /usr/autodesk/maya2013-x64/lib/libcrypto.so.6
fi
 
# libtiff
**sudo ln -s /usr/lib/x86_64-linux-gnu/libtiff.so.5.1.0 /usr/lib/x86_64-linux-gnu/libtiff.so.3**
sleep 2s
 
#Everything should work now...
echo "Installation Complete."
echo ""
echo "Start Maya Now?"
read RUNNOW
case "$RUNNOW" in
	n*|N*)
	echo "You can run maya any time by typing maya into the terminal"
	exit 0;
esac
maya


```

Any thoughts?

---

### Post by Toz on 2013-05-30
Just keep in mind that this script will only work with the libtiff package at version 5.1.0. Once that changes, the script will no longer work. Or rather, the script will work but the link won't be successful.

Perhaps a statement like this one would be better, since it would get the latest version of the installed libtiff package (based on date) and link to it:
```
sudo ln -s $(ls -lt /usr/lib/x86_64-linux-gnu/libtiff* | head -1 | cut -d' ' -f9) /usr/lib/x86_64-linux-gnu/libtiff.so.3
```

---

### Post by niallcd on 2013-05-30
So we can add that so it reads: 

```
 
# libtiff
sudo ln -s $(ls -lt /usr/lib/x86_64-linux-gnu/libtiff* | head -1 | cut -d' ' -f9) /usr/lib/x86_64-linux-gnu/libtiff.so.3

sleep 2s

```

Again, you've been a huge help on this issue. Thanks.

---

### Post by omarandreti on 2013-10-13
Hello! 
I'm experiencing exactly the same issues, and I've done everything in this forum. I tryed to run maya again after all of this from the terminal, typing simply maya, and nothing happens now. It would be great if I can get some help. Thank you!

This is what I've done in the terminal:

a3dworkshop@a3dworkshop-System-Product-Name:~$ ls -l /usr/lib/x86_64-linux-gnu/libtiff.so.3
lrwxrwxrwx 1 root root 42 Oct 13 19:25 /usr/lib/x86_64-linux-gnu/libtiff.so.3 -> /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
a3dworkshop@a3dworkshop-System-Product-Name:~$ ls -l /usr/lib/x86_64-linux-gnu/libjpeg.so.62
lrwxrwxrwx 1 root root 42 Oct 13 19:26 /usr/lib/x86_64-linux-gnu/libjpeg.so.62 -> /usr/lib/x86_64-linux-gnu/libjpeg.so.8.0.2
a3dworkshop@a3dworkshop-System-Product-Name:~$ ldd /usr/autodesk/maya2014-x64/bin/maya.bin
    linux-vdso.so.1 =>  (0x00007fffed249000)
    libMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libMaya.so (0x00007fee55d2a000)
    libawxml2.so => /usr/autodesk/maya2014-x64/bin/../lib/libawxml2.so (0x00007fee55a05000)
    libIMFbase.so => /usr/autodesk/maya2014-x64/bin/../lib/libIMFbase.so (0x00007fee5575d000)
    libawMarkingMenus.so => /usr/autodesk/maya2014-x64/bin/../lib/libawMarkingMenus.so (0x00007fee5552a000)
    libAG.so => /usr/autodesk/maya2014-x64/bin/../lib/libAG.so (0x00007fee54f17000)
    libiff.so => /usr/autodesk/maya2014-x64/bin/../lib/libiff.so (0x00007fee54ce0000)
    libawGR.so => /usr/autodesk/maya2014-x64/bin/../lib/libawGR.so (0x00007fee54ad0000)
    libAppVersion.so => /usr/autodesk/maya2014-x64/bin/../lib/libAppVersion.so (0x00007fee548cf000)
    libFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libFoundation.so (0x00007fee54331000)
    libAnimEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimEngine.so (0x00007fee54097000)
    libCommandEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libCommandEngine.so (0x00007fee53d7a000)
    libDependEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependEngine.so (0x00007fee53880000)
    libGeometryEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryEngine.so (0x00007fee53623000)
    libNurbsEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsEngine.so (0x00007fee53222000)
    libImage.so => /usr/autodesk/maya2014-x64/bin/../lib/libImage.so (0x00007fee52f93000)
    libDependCommand.so => /usr/autodesk/maya2014-x64/bin/../lib/libDependCommand.so (0x00007fee52d65000)
    libExtensionLayer.so => /usr/autodesk/maya2014-x64/bin/../lib/libExtensionLayer.so (0x00007fee52627000)
    libDataModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libDataModel.so (0x00007fee51c46000)
    libPolyEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolyEngine.so (0x00007fee5168e000)
    lib3dGraphics.so => /usr/autodesk/maya2014-x64/bin/../lib/lib3dGraphics.so (0x00007fee5141d000)
    libNurbs.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbs.so (0x00007fee5107b000)
    libRenderModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderModel.so (0x00007fee506d5000)
    libPoly.so => /usr/autodesk/maya2014-x64/bin/../lib/libPoly.so (0x00007fee502fe000)
    libShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libShared.so (0x00007fee4f7cd000)
    libPolySlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libPolySlice.so (0x00007fee4f164000)
    libSharedUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libSharedUI.so (0x00007fee4e7a5000)
    libHWFoundation.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWFoundation.so (0x00007fee4e558000)
    libHWGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWGL.so (0x00007fee4e2e7000)
    libHWRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRender.so (0x00007fee4e079000)
    libHWRenderMaya.so => /usr/autodesk/maya2014-x64/bin/../lib/libHWRenderMaya.so (0x00007fee4dddf000)
    libOGSRender.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSRender.so (0x00007fee4d948000)
    libOGSMayaBridge.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMayaBridge.so (0x00007fee4d384000)
    libRenderSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libRenderSlice.so (0x00007fee4ce1d000)
    libMetaData.so => /usr/autodesk/maya2014-x64/bin/../lib/libMetaData.so (0x00007fee4cbbc000)
    libDeformSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDeformSlice.so (0x00007fee4c6ad000)
    libModelSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libModelSlice.so (0x00007fee4c3a0000)
    libNurbsSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libNurbsSlice.so (0x00007fee4bdff000)
    libAnimSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libAnimSlice.so (0x00007fee4b864000)
    libKinSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libKinSlice.so (0x00007fee4afc2000)
    libTranslators.so => /usr/autodesk/maya2014-x64/bin/../lib/libTranslators.so (0x00007fee4ad43000)
    libBase.so => /usr/autodesk/maya2014-x64/bin/../lib/libBase.so (0x00007fee4aa0b000)
    libadlmint.so.7 => /usr/autodesk/maya2014-x64/bin/../lib/libadlmint.so.7 (0x00007fee4a417000)
    libQtCore.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtCore.so.4 (0x00007fee49f14000)
    libQtGui.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtGui.so.4 (0x00007fee491c4000)
    libQtSvg.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtSvg.so.4 (0x00007fee48f64000)
    libGLU.so.1 => /usr/lib/x86_64-linux-gnu/libGLU.so.1 (0x00007fee48cdc000)
    libGL.so.1 => /usr/lib/nvidia-304/libGL.so.1 (0x00007fee489bf000)
    libXm.so.3 => /usr/autodesk/maya2014-x64/bin/../lib/libXm.so.3 (0x00007fee48630000)
    libXp.so.6 => /usr/lib/x86_64-linux-gnu/libXp.so.6 (0x00007fee48427000)
    libXmu.so.6 => /usr/lib/x86_64-linux-gnu/libXmu.so.6 (0x00007fee4820e000)
    libXpm.so.4 => /usr/lib/x86_64-linux-gnu/libXpm.so.4 (0x00007fee47ffc000)
    libXt.so.6 => /usr/lib/x86_64-linux-gnu/libXt.so.6 (0x00007fee47d96000)
    libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007fee47b87000)
    libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fee47975000)
    libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fee47640000)
    libimf.so => /usr/autodesk/maya2014-x64/bin/../lib/libimf.so (0x00007fee47274000)
    libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fee46f77000)
    libtbb.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbb.so.2 (0x00007fee46e2a000)
    libtbbmalloc.so.2 => /usr/autodesk/maya2014-x64/bin/../lib/libtbbmalloc.so.2 (0x00007fee46ce6000)
    libsvml.so => /usr/autodesk/maya2014-x64/bin/../lib/libsvml.so (0x00007fee4656b000)
    libiomp5.so => /usr/autodesk/maya2014-x64/bin/../lib/libiomp5.so (0x00007fee4627d000)
    libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fee45f7d000)
    libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fee45d66000)
    libintlc.so.5 => /usr/autodesk/maya2014-x64/bin/../lib/libintlc.so.5 (0x00007fee45c17000)
    libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fee459fa000)
    libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fee4563a000)
    libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fee45436000)
    libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fee4521e000)
    libawDebugTools.so => /usr/autodesk/maya2014-x64/bin/../lib/libawDebugTools.so (0x00007fee4501a000)
    libQtOpenGL.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtOpenGL.so.4 (0x00007fee44d0d000)
    libsynHub.so => /usr/autodesk/maya2014-x64/bin/../lib/libsynHub.so (0x00007fee4475c000)
    libpython2.7.so.1.0 => /usr/autodesk/maya2014-x64/bin/../lib/libpython2.7.so.1.0 (0x00007fee44390000)
    libquicktime.so.0 => /usr/autodesk/maya2014-x64/bin/../lib/libquicktime.so.0 (0x00007fee440d1000)
    libQtWebKit.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtWebKit.so.4 (0x00007fee424d6000)
    libQtNetwork.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtNetwork.so.4 (0x00007fee42175000)
    libQtScript.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtScript.so.4 (0x00007fee41cab000)
    libtiff.so.3 => /usr/lib/x86_64-linux-gnu/libtiff.so.3 (0x00007fee41a46000)
    libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007fee41843000)
    libPtex.so => /usr/autodesk/maya2014-x64/bin/../lib/libPtex.so (0x00007fee415ab000)
    libawCacheShared.so => /usr/autodesk/maya2014-x64/bin/../lib/libawCacheShared.so (0x00007fee4138b000)
    libQtXml.so.4 => /usr/autodesk/maya2014-x64/bin/../lib/libQtXml.so.4 (0x00007fee41141000)
    libfbxassetscore2.so => /usr/autodesk/maya2014-x64/bin/../lib/libfbxassetscore2.so (0x00007fee40dbb000)
    libopenal.so.1 => /usr/autodesk/maya2014-x64/bin/../lib/libopenal.so.1 (0x00007fee40b6b000)
    libfam.so.0 => /usr/lib/libfam.so.0 (0x00007fee40963000)
    libGeometryDefn.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryDefn.so (0x00007fee40718000)
    libGeometryAlg.so => /usr/autodesk/maya2014-x64/bin/../lib/libGeometryAlg.so (0x00007fee403e2000)
    libTesselation.so => /usr/autodesk/maya2014-x64/bin/../lib/libTesselation.so (0x00007fee40112000)
    libawnSolver.so => /usr/autodesk/maya2014-x64/bin/../lib/libawnSolver.so (0x00007fee3fd40000)
    libSubdivEngine.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivEngine.so (0x00007fee3fa8f000)
    libSubdivGeom.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdivGeom.so (0x00007fee3f822000)
    libSubdiv.so => /usr/autodesk/maya2014-x64/bin/../lib/libSubdiv.so (0x00007fee3f46c000)
    libDynSlice.so => /usr/autodesk/maya2014-x64/bin/../lib/libDynSlice.so (0x00007fee3eafb000)
    libadp_core-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_core-4_0.so (0x00007fee3e772000)
    libadp_data-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_data-4_0.so (0x00007fee3e503000)
    libadp_service_opczip-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_service_opczip-4_0.so (0x00007fee3e2e8000)
    libadp_toolkit-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libadp_toolkit-4_0.so (0x00007fee3de4f000)
    libMgMdfModel.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfModel.so (0x00007fee3dbdd000)
    libMgMdfParser.so => /usr/autodesk/maya2014-x64/bin/../lib/libMgMdfParser.so (0x00007fee3d8ff000)
    libOGSAtilIntegration-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSAtilIntegration-4_0.so (0x00007fee3ce31000)
    libOGSDevices-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDevices-4_0.so (0x00007fee3c694000)
    libOGSGraphics-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSGraphics-4_0.so (0x00007fee3bc9b000)
    libOGSObjects-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSObjects-4_0.so (0x00007fee3b8ab000)
    libOGSMgStylization-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSMgStylization-4_0.so (0x00007fee3b525000)
    libOGSDeviceOGL-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSDeviceOGL-4_0.so (0x00007fee3b272000)
    libweightXML.so => /usr/autodesk/maya2014-x64/bin/../lib/libweightXML.so (0x00007fee3b06d000)
    libManips.so => /usr/autodesk/maya2014-x64/bin/../lib/libManips.so (0x00007fee3ab74000)
    libImageUI.so => /usr/autodesk/maya2014-x64/bin/../lib/libImageUI.so (0x00007fee3a746000)
    libModifiers.so => /usr/autodesk/maya2014-x64/bin/../lib/libModifiers.so (0x00007fee3a3b4000)
    librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fee3a1aa000)
    libuuid.so.1 => /lib/x86_64-linux-gnu/libuuid.so.1 (0x00007fee39fa5000)
    libgthread-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0 (0x00007fee39da2000)
    libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fee39aad000)
    /lib64/ld-linux-x86-64.so.2 (0x00007fee55f2d000)
    libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fee39884000)
    libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fee395e8000)
    libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fee39399000)
    libSM.so.6 => /usr/lib/x86_64-linux-gnu/libSM.so.6 (0x00007fee39191000)
    libICE.so.6 => /usr/lib/x86_64-linux-gnu/libICE.so.6 (0x00007fee38f76000)
    libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007fee38d6c000)
    libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fee38b36000)
    libnvidia-tls.so.304.88 => /usr/lib/nvidia-304/tls/libnvidia-tls.so.304.88 (0x00007fee38932000)
    libnvidia-glcore.so.304.88 => /usr/lib/nvidia-304/libnvidia-glcore.so.304.88 (0x00007fee36548000)
    libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fee36344000)
    libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fee36126000)
    libutil.so.1 => /lib/x86_64-linux-gnu/libutil.so.1 (0x00007fee35f22000)
    libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007fee35bd3000)
    libgstapp-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstapp-0.10.so.0 (0x00007fee359c6000)
    libgstinterfaces-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstinterfaces-0.10.so.0 (0x00007fee357b4000)
    libgstpbutils-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstpbutils-0.10.so.0 (0x00007fee35591000)
    libgstvideo-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstvideo-0.10.so.0 (0x00007fee35374000)
    libgstbase-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstbase-0.10.so.0 (0x00007fee35121000)
    libgstreamer-0.10.so.0 => /usr/lib/x86_64-linux-gnu/libgstreamer-0.10.so.0 (0x00007fee34e3a000)
    libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fee34c35000)
    libxml2.so.2 => /usr/lib/x86_64-linux-gnu/libxml2.so.2 (0x00007fee348d9000)
    libjpeg.so.8 => /usr/lib/x86_64-linux-gnu/libjpeg.so.8 (0x00007fee34688000)
    libxerces-c.so.27 => /usr/autodesk/maya2014-x64/bin/../lib/libxerces-c.so.27 (0x00007fee34072000)
    libOGSArchive-4_0.so => /usr/autodesk/maya2014-x64/bin/../lib/libOGSArchive-4_0.so (0x00007fee33e40000)
    libNsArchive10.so => /usr/autodesk/maya2014-x64/bin/../lib/libNsArchive10.so (0x00007fee33c3b000)
    libssl.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libssl.so.10 (0x00007fee339ec000)
    libcrypto.so.10 => /usr/autodesk/maya2014-x64/bin/../lib/libcrypto.so.10 (0x00007fee33698000)
    libCg.so => /usr/autodesk/maya2014-x64/bin/../lib/libCg.so (0x00007fee321be000)
    libCgGL.so => /usr/autodesk/maya2014-x64/bin/../lib/libCgGL.so (0x00007fee3203a000)
    libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fee31dfc000)
    libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fee31bf3000)
    libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fee319c9000)
    libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fee317c2000)
    libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fee315a3000)
    libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fee31387000)
    liborc-0.4.so.0 => /usr/lib/x86_64-linux-gnu/liborc-0.4.so.0 (0x00007fee3110b000)
    libziparch.so => /usr/autodesk/maya2014-x64/bin/../lib/libziparch.so (0x00007fee30e43000)
    libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fee30c05000)
    libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fee30937000)
    libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fee30732000)
    libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fee3050a000)
    libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fee30301000)
    libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fee300fd000)
a3dworkshop@a3dworkshop-System-Product-Name:~$ ls -l /usr/lib/x86_64-linux-gnu/libtiff*
lrwxrwxrwx 1 root root     42 Oct 13 19:25 /usr/lib/x86_64-linux-gnu/libtiff.so.3 -> /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
lrwxrwxrwx 1 root root     16 May 13 13:22 /usr/lib/x86_64-linux-gnu/libtiff.so.4 -> libtiff.so.4.3.4
-rw-r--r-- 1 root root 408072 May 13 13:22 /usr/lib/x86_64-linux-gnu/libtiff.so.4.3.4
a3dworkshop@a3dworkshop-System-Product-Name:~$ maya

---

### Post by brycehenley97 on 2013-10-27
The script is for Maya 2013 not 2014. I ran it on Ubuntu 13.01 and it did not install. Here is the terminal output, hope it is some help.


maya.sh: line 9: [uname: command not found
You’re about to download and install Autodesk Maya 2013

Do you wish to continue [Y/n]?
y
If you have not already done so, you can get your serial number from: [http://students.autodesk.com](http://students.autodesk.com)
Enter the serial number
************

Creating mayaTempInstall folder

maya.sh: line 47: cd: /home/bryce/MAYAINSTALL: No such file or directory
--2013-10-27 14:23:07--  [http://download.autodesk.com/us/maya/service_packs/Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz](http://download.autodesk.com/us/maya/service_packs/Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz)
Resolving download.autodesk.com (download.autodesk.com)... 184.180.124.122, 184.180.124.59
Connecting to download.autodesk.com (download.autodesk.com)|184.180.124.122|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 798135468 (761M) [text/plain]
Saving to: ‘Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz’

100%[======================================>] 798,135,468  544KB/s   in 13m 2s 

2013-10-27 14:36:09 (997 KB/s) - ‘Autodesk_Maya_2013_SP1_English_Linux_64bit.tgz’ saved [798135468/798135468]

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ttf-liberation is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'ttf-liberation' has no installation candidate
tar: /home/bryce/MAYAINSTALL/Autodesk*.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
maya.sh: line 61: syntax error near unexpected token `do'
maya.sh: line 61: `sudo for i in $INSTALLDIR/*.rpm; do sudo alien -cv $i; done'

---

### Post by MikeCyber on 2014-08-29
How/where do you enter your code? It says click activate and paste something which I cannot find.
Thanks
PS: is there a 2015 version for Linux?

---

### Post by MikeCyber on 2014-08-30
Well work around was installing 2014 in win8.1 and I got it in Linux as well. But now while trying to open another scene I get:

michael@michael-ubuntu:~$ maya

libGL error: dlopen /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: undefined symbol: _glapi_tls_Dispatch)
libGL error: dlopen ${ORIGIN}/dri/swrast_dri.so failed (/usr/lib/x86_64-linux-gnu/dri/swrast_dri.so: undefined symbol: _glapi_tls_Dispatch)
libGL error: dlopen /usr/lib/dri/swrast_dri.so failed (/usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory)
libGL error: unable to load driver: swrast_dri.so
libGL error: failed to load driver: swrast
mental ray for Maya 2014 
mental ray: version 3.11.1.4, Jan 25 2013, revision 189569

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/michael.20140830.1908.ma
michael@michael-ubuntu:~$ 

Thanks

---

### Post by thenox on 2014-09-09
Were you able to resolve this? I'm going to be installing Maya on Linux soon, and I may run into the same issue. 

Any tips or tricks to watch out for? 

Thank you.

---

### Post by uRock on 2014-09-09
> **MikeCyber said:**
> How/where do you enter your code? It says click activate and paste something which I cannot find.
Thanks
PS: is there a 2015 version for Linux?

Instead of rebirthing a thread from last year, you should've created a new thread. You'd likely get more responses.

Cheers & Beers,
uRock

---

