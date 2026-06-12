---
title: "Problem trying to install mathbuntu"
date: 2014-07-09
forum: General Help
---

### Post by will-earnshaw on 2014-07-09
Hi Everyone.

I am hoping to start a university degree in mathematics soon and I am quite interested in the mathbuntu distro.

The website suggests installing ubuntu/kdebuntu/lubuntu and then running an upgrade script as its download server is slow.

I have an old netbook that I put a fresh install of lubuntu on and I have downloaded the upgrade, the website says to drag one file onto another but whenever I try to do that I get an error box saying "Failed to change directory ''(no such file or directory)".

I'm pretty new to scripts but I'm guessing it might need root access but I don't know how to give it that outside of the terminal.

Here is a link to the script download, its quite small: [http://www.mathbuntu.org/index.html?open=download](http://www.mathbuntu.org/index.html?open=download)

Any help will be greatly appreciated. Many thanks in advance!

---

### Post by yancek on 2014-07-09
You could open a terminal and try:  sudo pcmanfm.  I beleive pcmanfm is the default file manager for Lubuntu.  I don't use Lubuntu but I seem to remember that working in the past.

---

### Post by will-earnshaw on 2014-07-09
> **yancek said:**
> You could open a terminal and try:  sudo pcmanfm.  I beleive pcmanfm is the default file manager for Lubuntu.  I don't use Lubuntu but I seem to remember that working in the past.

Thanks for a quick reply.

I tried that and it did indeed open an instance of my file manager, this is new to me, I had no idea that you could launch gui programs from the terminal, i thought it only delt with command line stuff. 

I tried it again with the new file manager window but I got the same error unfortunatly. I don't know if doing this just made the file manager root but not the items inside it? Do the files inside a root file manager inheret the root privaleges? 

Cheers

---

### Post by oldfred on 2014-07-09
No, just using a gui at root does not make every thing you use or look  at be root also.
I only use Ubuntu and in Nautilus you can set permission to execute to allow running a program. Not sure if you file manager allows that or not.

Generally if you have an application you need to run you need to change its permissions. Make sure it is one you trust and know as that is a way for a scam to get you to run scripts that can damage system.

Usually you just set to executeable and run as root. Change example from bootinfoscript to your math installer script.
If necessary change to folder where you saved it, often Downloads which may look like ~/Downloads. ~ is a short for /home/$USER where $USER is your login name.
cd Downloads
       chmod a+x bootinfoscript
sudo bash bootinfoscript

---

### Post by will-earnshaw on 2014-07-09
Thanks Old Fred, I tried that but still no joy I'm afraid. Exactly the same error :(

We are starting to get into terratory that I don't really understand, however, I opened the script and found this following line of code: cd $(dirname $0)/.files

Now from what I understand, a folder that begins with a full stop (period) is hidden, and that might be where the error is coming from. Is this something that lubuntu hic ups on where as the other versions are fine? If I find the hidden folder and rename it may that solve the problem.

Many thanks

---

### Post by yancek on 2014-07-09
I'm not sure I'm understanding this.  The instructions on the site you posted and what you posted originally say that you drag the first file to the second and drop.  Are you seeing both files?  Don't see what difference it would make if it is a hidden file if you can see it to drag/drop as suggested.  Maybe we're missing something here?

---

### Post by will-earnshaw on 2014-07-09
I am dragging this file:

installMathbuntu
which contains:
```
#!/bin/bash

#                                                                          #
#  installMathbuntu is a script that will install mathematics related      #
#  software to an Ubuntu installation.                                     #
#  Copyright (C) 2010-2014  Leon Q. Brin                                   #
#                                                                          #
#  This script and accompanying files are free software; you can           #
#  redistribute it and/or modify it under the terms of the GNU General     #
#  Public License as published by the Free Software Foundation; either     #
#  version 2 of the License, or (at your option) any later version.        #
#                                                                          #
#  This program is distributed in the hope that it will be useful,         #
#  but WITHOUT ANY WARRANTY; without even the implied warranty of          #
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the           #
#  GNU General Public License for more details.                            #
#                                                                          #
#  You should have received a copy of the GNU General Public License       #
#  along with this program; if not, write to the Free Software Foundation, #
#  Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.     #
#                                                                          #
#  Written by Leon Q. Brin                                                 #
#  Last updated 29 April 2014                                              #
#                                                                          #

##################
# Set basic info #
##################
LOGFILE="mathbuntu.log"
cd $(dirname $0)/.files
verifyCount=0

###########################################
# Install critical installer applications #
###########################################
echo "Checking for prerequisite packages. Installing if necessary..."
echo "Subsequent dialogs may be graphical."
source ./installMethods.sh
installerApps="aria2 zenity"
trycommand "apt-get install -y $installerApps"
echo
ZENITY=`which zenity`

##########################
# Get system information #
##########################
processCommandLine $*
source ./getFlavor.sh
source ./getRelease.sh
source ./getArchitecture.sh
echo

#########
# Begin #
#########
msg="GREETINGS!

Welcome to the $FLAVOR $VERSION $ARCHITECTURE installer. Sit back and relax while your software is installed.

If you are not planning to keep your computer occupied while this script runs, you should <b>TURN OFF POWER MANAGEMENT</b>. The installation will take hours, and will be interrupted every 10 or 15 minutes by power savers that pause the machine due to \"inactivity\".

I will provide updates from time to time."
if [ ! -z "$ZENITY" ]; then
  if [ "$AUTOMATIC" == "yes" ]; then
    msg="$msg This dialog and subsequent newsflashes will disappear 60 seconds from the time they appear."
    timeout=""
  else
    msg="$msg Subsequent newshflashes will disappear 60 seconds from the time they appear."
    timeout="notimeout"
  fi
fi
newsflash "$msg" $timeout
date > $LOGFILE
date
echo
echo "Now that that's out of the way, we can begin with the"
echo "math$FLAVOR $VERSION installer!"
echo

######################
# Set some variables #
######################
source ./vars$VERSION.sh
# Textbooks and Documentation
htmlDestDir="$mathbuntuLocal/freebooks"
textbookDestDir="$mathbuntuLocal/freebooks/pdfs"
textbook=( $(cat "./textbook.list" | grep -v -E "^#") )
documentationDestDir="$mathbuntuLocal/freebooks/pdfs"
geogebraDocList="./geogebraDoc.list"
maximaDocList="./wxmaximaDoc.list"
sageDocList="./sageDoc.list"
rDocList="./rDoc.list"

#########################
# Make some directories #
#########################
makedirectory "$mathbuntuLocal"
makedirectory "$htmlDestDir"
makedirectory "$textbookDestDir"
makedirectory "$documentationDestDir"

#####################
# Update repository #
#####################
newsflash "Updating package repository..."
trycommand "apt-get update -y"
echo
# Upgrade if requested
if [ "$UPGRADE" == "yes" ]; then
  newsflash "Upgrading installed packages..."
  echo
  trycommand "apt-get dist-upgrade -y"
  echo
fi

##################
# Install Octave #
##################
newsflash "Checking currently installed software versions..."
if installOctave; then
  newsflash "Compiling Octave in the background..."
  makeTempUser
  trycommand "apt-get install -y $compileApps $compileOctaveApps"
  trycommand "wget -P /tmp $octaveServer"
  ./compileOctave.sh $octaveFile $octaveDir > /tmp/octaveCompile.log 2>&1 &
  octavePid=$!
  echo "with PID $octavePid"
fi
echo

##################
# Install Maxima #
##################
if installMaxima; then
  newsflash "Compiling Maxima in the background..."
  makeTempUser
  trycommand "apt-get install -y $compileApps $compileMaximaApps"
  trycommand "wget -P /tmp $maximaServer"
  ./compileMaxima.sh $maximaFile $maximaDir > /tmp/maximaCompile.log 2>&1 &
  maximaPid=$!
  echo "with PID $maximaPid"
fi
echo

####################
# Install wxMaxima #
####################
if installWxmaxima; then
  newsflash "Compiling wxMaxima in the background..."
  makeTempUser
  makedirectory "$mathbuntuLocal/wxMaxima"
  trycommand "apt-get install -y $compileApps $compileWxmaximaApps"
  trycommand "wget -P /tmp $wxmaximaServer"
  ./compileWxmaxima.sh $wxmaximaFile $wxmaximaDir > /tmp/wxmaximaCompile.log 2>&1 &
  wxmaximaPid=$!
  echo "with PID $wxmaximaPid"
fi
echo

##################
# Install Xppaut #
##################
trycommand "mkdir -p $mathbuntuLocal/$xppautDir"
if installXppaut; then
  newsflash "Compiling xppaut from source..."
  makeTempUser
  trycommand "apt-get install -y $compileApps"
  trycommand "wget -P /tmp $xppautServer/$xppautFile"
  ./compileXppaut.sh $xppautFile $xppautDir $mathbuntuLocal> /tmp/xppautCompile.log 2>&1
  echo "Done. See /tmp/xppautCompile.log for details."
fi
if checkMd5sum "$mathbuntuLocal/$xppautDir/$xppautIcon" $xppautIconMd5sum; then
  echo "xppaut icon is already installed."
else
  echo "Installing xppaut icon..."
  trycommand "wget -P /tmp $xppautServer/binary/$xppautIcon"
  trycommand "cp /tmp/$xppautIcon $mathbuntuLocal/$xppautDir"
fi
echo

#################
# Install Lurch #
#################
if installLurch; then
  newsflash "Compiling lurch in the background..."
  makedirectory "$mathbuntuLocal/lurch"
  trycommand "apt-get install -y $compileApps $compileLurchApps"
  ./compileLurch.sh $lurchCandidateVersion "$lurchServer" > /tmp/lurchCompile.log 2>&1 &
  lurchPid=$!
  echo "with PID $lurchPid"
fi
echo

################
# Install Sage #
################
if installSage; then
  newsflash "Compiling sage in the background..."
  makeTempUser
  trycommand "apt-get install -y $compileApps $compileSageApps"
  trycommand "wget -P /tmp $sageServer"
  trycommand "aria2c -d /tmp --seed-time=0 /tmp/$sageMetaFile"
  ./compileSage.sh "$sageFile" "$sageDir" "$mathbuntuLocal" > /tmp/sageCompile.log 2>&1 &
  sagePid=$!
  echo "with PID $sagePid"
fi
echo

#####################################################
# Install non-mathematical software from repository #
#####################################################
newsflash "Installing non-mathematical packages..."
trycommand "apt-get install -y $nonmathApps"
echo

#################################################
# Install mathematical software from repository #
#################################################
newsflash "Installing mathematical packages..."
trycommand "apt-get install -y $commonMathApps"
if [ $FLAVOR != "Lubuntu" ]; then
  trycommand "apt-get install -y $heavyMathApps"
fi
echo

####################################################
# Install flavor-specific software from repository #
####################################################
newsflash "Installing flavor-specific software..."
if [ $FLAVOR == "Ubuntu" ]; then
  trycommand "apt-get install -y $gnomeApps"
else
  if [ $FLAVOR == "Kubuntu" ]; then
    trycommand "apt-get install -y $kdeApps"
  fi
fi
echo

#############################
# Install Mathbuntu tarball #
#############################
echo "Creating backup files..."
# mozpluggerrc
fn="/etc/mozpluggerrc"
if [ -f $fn ]; then
  trycommand "mv -n $fn $fn.mathbuntuSave"
fi
# 62-documents.conf
fn="/etc/mozpluggerrc.d/62-documents.conf"
if [ -f $fn ]; then
  trycommand "mv -n $fn $fn.mathbuntuSave"
fi
echo
if installCustomFiles; then
  newsflash "Installing custom files..."
  mathbuntuTarball="mathbuntu$VERSION.tar.gz"
    trycommand "aria2c -d /tmp http://www.mathbuntu.org/tarball/$mathbuntuTarball"
    trycommand "tar -C / --no-same-owner -xzvf /tmp/$mathbuntuTarball"
  if checkMd5sum "/tmp/$mathbuntuTarball" $mathbuntuTarballMd5sum; then
    echo "$mathbuntuTarballMd5sum" > $mathbuntuCheckFile
  fi
fi
echo

#####################
# Install textbooks #
#####################
newsflash "Installing textbooks..."
htmlDest="./textIndex.html"
cp -f ./textHead.html $htmlDest
numTexts=$(( ${#textbook[@]} / 10 ))
echoTableStart >> $htmlDest
lastCategory="none"
for (( i = 0 ; i < $numTexts ; i++ ))
do
  subdir=`echo ${textbook[10*i+9]} | sed 's/_//g'`
  textbookSubdir="$textbookDestDir/$subdir"
  category=`echo ${textbook[10*i+9]} | sed 's/_/ /g'`
  if [ "$category" != "$lastCategory" ]; then
    echo "<tr><td colspan=\"5\" style=\"text-align:center; font-weight:bold;\"><br /><big>$category</big></td></tr>" >> $htmlDest
    if [ -e "$textbookSubdir" ] && [ ! -d "$textbookSubdir" ]; then
      rm -f "$textbookSubdir"
    fi
    if [ ! -e "$textbookSubdir" ]; then
      mkdir -p "$textbookSubdir"
    fi
  fi
  destPath=$textbookSubdir/${textbook[10*i+5]}
  md5sum=${textbook[10*i+8]}
  if checkMd5sum $destPath $md5sum; then
    echo "${textbook[10*i+5]} is already installed."
  else
    downloadURL=${textbook[10*i+1]}
    sourceName=${textbook[10*i+4]}
    if [ ${textbook[10*i+1]:0:4} == "WGET" ]; then
      com="wget -P"
      downloadURL=${textbook[10*i+1]:4}
    else
      com="aria2c -d"
    fi
    cp -f ./pdfNotAvailable.pdf $destPath
    trycommand "$com /tmp $downloadURL"
    trycommand "mv -f /tmp/$sourceName $destPath"
    verifyList[4*$verifyCount]=$destPath
    verifyList[4*$verifyCount+1]=$md5sum
    verifyList[4*$verifyCount+2]=$downloadURL
    verifyList[4*$verifyCount+3]=$sourceName
    verifyCount=$(( $verifyCount + 1 ))
  fi
  echo "<tr><td></td>" >> $htmlDest
  echo "<td><a target=\"_blank\" href=\"${textbook[10*i]}\"><span class=\"headword\">${textbook[10*i+6]}</span><br>${textbook[10*i+7]}</a></td>" >> $htmlDest
  echo "<td style=\"text-align: center;\"><a target=\"_blank\" href=\"pdfs/$subdir/${textbook[10*i+5]}\"><img border=\"0\" src=\"/usr/local/share/mathbuntu/acroread/acroread.png\"></a></td>" >> $htmlDest
  echo "<td style=\"text-align: center;\"><a target=\"_blank\" href=\"${textbook[10*i+2]}\"><img border=\"0\" src=\"${textbook[10*i+3]}\"></a></td>" >> $htmlDest
  echo "<td><br></td></tr>" >> $htmlDest
  lastCategory=$category
done
echoTableEnd >> $htmlDest
cp -f $htmlDest $htmlDestDir
echo

##################################
# Install software documentation #
##################################
newsflash "Installing software documentation..."
# Geogebra
echo "Installing Geogebra documentation..."
installDocumentation $geogebraDocList "./geogebraHead.html" "./geogebraIndex.html" $htmlDestDir $documentationDestDir "GeoGebra"
echo
# Maxima
echo "Installing Maxima documentation..."
trycommand "cp wxmaximaSamples.html $htmlDestDir"
installDocumentation $maximaDocList "./wxmaximaHead.html" "./wxmaximaIndex.html" $htmlDestDir $documentationDestDir "Maxima"
echo
# R
echo "Installing R documentation..."
installDocumentation $rDocList "./rHead.html" "./rIndex.html" $htmlDestDir $documentationDestDir "R"
echo
# SAGE
echo "Installing SAGE documentation..."
installDocumentation $sageDocList "./sageHead.html" "./sageIndex.html" $htmlDestDir $documentationDestDir "Sage"
echo

######################
# Install other apps #
######################
# GeoGebra
if installGeogebra; then
  newsflash "Installing GeoGebra..."
  trycommand "aria2c -d /tmp $geogebraServer/$geogebraPackageName/$geogebraFileName"
  trycommand "apt-get remove -y geogebra"
  trycommand "apt-get remove -y $geogebraPackageName"
  trycommand "dpkg -i /tmp/geogebra*deb"
fi
echo
# Rstudio
if installRstudio; then
  newsflash "Installing Rstudio"
  trycommand "apt-get install -y $rstudioDependencies"
  trycommand "aria2c -d /tmp $rstudioServer$rstudioFile"
  trycommand "dpkg -i /tmp/$rstudioFile"
fi
echo
# NetLogo
if installNetlogo; then
  newsflash "Installing NetLogo"
  trycommand "aria2c -d /tmp $netlogoServer/$netlogoFile"
  trycommand "tar -C $mathbuntuLocal --no-same-owner -xzf /tmp/$netlogoFile"
  echo "#!/bin/bash" > /usr/local/bin/netlogo
  echo "cd $mathbuntuLocal/$netlogoDir && ./netlogo.sh" >> /usr/local/bin/netlogo
  chmod 755 /usr/local/bin/netlogo
  echo "$netlogoCandidateVersion" > "$mathbuntuLocal/$netlogoDir/version"
fi
# Jslideshow:
echo "Installing Jslideshow..."
trycommand "aria2c -d /tmp http://sourceforge.net/projects/jslideshow/files/jslideshow-installer/0.92/UbuntuInstaller.tar.gz/download"
trycommand "tar -C /tmp -xzvf /tmp/UbuntuInstaller.tar.gz"
trycommand "/tmp/Jslideshow-installer/installJslideshow skipupdate"
echo
# Plop Boot Manager:
echo "Installing Plop Boot Manager..."
updateGrub="no"
if [ ! -f /boot/plpbt.bin ]; then
  trycommand "aria2c -d /tmp $plopServer"
  trycommand "unzip -d /tmp -o /tmp/$plopFile"
  trycommand "cp /tmp/$plopDir/plpbt.bin /boot"
  updateGrub="yes"
fi
alreadyIn=`grep "Plop Boot Manager" $customGrubFile`
if [ -z "$alreadyIn" ]; then
  echo "Adding custom entry to grub menu."
  echo 'menuentry "Use Plop Boot Manager" {' >> $customGrubFile
  echo '    set root=(hd0,1)' >> $customGrubFile
  echo '    linux16 /boot/plpbt.bin' >> $customGrubFile
  echo '}' >> $customGrubFile
  updateGrub="yes"
  echo
fi
if [ $updateGrub == "yes" ]; then
  echo "Updating grub."
  trycommand "update-grub"
  echo
fi
echo
# Pidgin LaTeX:
if installPidginLatex; then
  newsflash "Installing Pidgin LaTeX..."
  makeTempUser
  trycommand "apt-get install -y $compileApps $compilePidginLatexApps"
  trycommand "aria2c -d /tmp $pidginLatexServer"
  echo "Compiling Pidgin-LaTeX from source..."
  ./compilePidginLatex.sh $pidginLatexFile $pidginLatexDir > /tmp/pidginLatexCompile.log 2>&1
  echo "Done. See /tmp/pidginLatexCompile.log for details."
fi
echo

newsflash "Tying up loose ends. Installation is almost complete..."
############################
# Create wxMaxima mimetype #
############################
echo "Creating wxMaxima mimetype..."
installMaximaMimetype=`find /usr/share/icons -name wxmaxima\*`
if [ -z "$installMaximaMimetype" ]; then
  trycommand "xdg-mime install --mode system --novendor wxmaxima.xml"
  size="128 64 48 32 16"
  for s in $size; do
    trycommand "xdg-icon-resource install --noupdate --context mimetypes --theme hicolor --size $s --novendor --mode system wxmaxima$s.png application-x-wxmaxima"
    trycommand "xdg-icon-resource install --noupdate --context apps --size $s --novendor --mode system wxmaxima$s.png wxmaxima"
  done
  trycommand "update-mime"
  trycommand "update-icon-caches /usr/share/icons/hicolor/"
fi
echo

#########################
# Create Lurch mimetype #
#########################
echo "Creating Lurch mimetype..."
installLurchMimetype=`find /usr/share/icons -name lurch\*`
if [ -z "$installLurchMimetype" ]; then
  trycommand "xdg-mime install --mode system --novendor lurch.xml"
  size="128 64 48 32 16"
  for s in $size; do
    trycommand "xdg-icon-resource install --noupdate --context mimetypes --theme hicolor --size $s --novendor --mode system lurch$s.png application-x-lurch"
    trycommand "xdg-icon-resource install --noupdate --context apps --size $s --novendor --mode system lurch$s.png lurch"
  done
  trycommand "update-mime"
  trycommand "update-icon-caches /usr/share/icons/hicolor/"
fi
echo

########################
# Create sage mimetype #
########################
echo "Creating sage mimetype..."
installSageMimetype=`find /usr/share/icons -name sagemath.png`
if [ -z "$installSageMimetype" ]; then
  trycommand "xdg-mime install --mode system --novendor sagemath.xml"
  size="128 64 48 32 16"
  for s in $size; do
    trycommand "xdg-icon-resource install --noupdate --context mimetypes --theme hicolor --size $s --novendor --mode system sagemath$s.png application-x-sagemath"
    trycommand "xdg-icon-resource install --noupdate --context apps --size $s --novendor --mode system sagemath$s.png sagemath"
  done
  trycommand "update-mime"
  trycommand "update-icon-caches /usr/share/icons/hicolor/"
fi
echo

##########################
# Create octave mimetype #
##########################
echo "Creating octave mimetype..."
installOctaveMimetype=`find /usr/share/icons -name octave.png`
if [ -z "$installOctaveMimetype" ]; then
  trycommand "xdg-mime install --mode system --novendor octave.xml"
  size="128 64 48 32 16"
  for s in $size; do
    trycommand "xdg-icon-resource install --noupdate --context mimetypes --theme hicolor --size $s --novendor --mode system octave$s.png application-x-octave"
    trycommand "xdg-icon-resource install --noupdate --context apps --size $s --novendor --mode system octave$s.png octave"
  done
  trycommand "update-mime"
  trycommand "update-icon-caches /usr/share/icons/hicolor/"
fi
echo

###########################
# Fix broken dependencies #
###########################
echo "Fixing any possible broken dependencies..."
trycommand "apt-get -y -f install"
trycommand "apt-get -y autoremove"
echo

###############################
# Run any extra configuration #
###############################
# Update mozplugger
echo "Updating mozpluggerrc..."
if float_cond "$VERSION > 11.0"; then
  trycommand "update-mozpluggerrc"
fi
echo
echo "Creating desktop shortcuts..."
  mkdir -p /etc/skel/Desktop/Online\ Resources
  doctorDesktopItem "firefox.desktop"
  doctorDesktopItem "freebooks.desktop"
  doctorDesktopItem "geogebra.desktop"
  doctorDesktopItem "kate.desktop"
  doctorDesktopItem "libreoffice-startcenter.desktop"
  doctorDesktopItem "lurch.desktop"
  doctorDesktopItem "lyx.desktop"
  doctorDesktopItem "octave.desktop"
  doctorDesktopItem "rstudio.desktop"
  doctorDesktopItem "netlogo.desktop"
  doctorDesktopItem "sagemath.desktop"
  doctorDesktopItem "wxmaxima.desktop"
  doctorDesktopItem "aim.desktop" "Online Resources"
  doctorDesktopItem "cuttheknot.desktop" "Online Resources"
  doctorDesktopItem "khanacademy.desktop" "Online Resources"
  doctorDesktopItem "myopenmath.desktop" "Online Resources"
  doctorDesktopItem "ocw.desktop" "Online Resources"
  doctorDesktopItem "sageonline.desktop" "Online Resources"
  doctorDesktopItem "saylor.desktop" "Online Resources"
  doctorDesktopItem "wolframalpha.desktop" "Online Resources"
echo

#######################################
# Copy skeleton into user directories #
#######################################
echo "Copying skeleton user experience..."
users=`ls /home`
for u in $users; do
  su $u -c "cp -rn /etc/skel/Desktop /home/$u/"
  su $u -c "cp -rn /etc/skel/.purple /home/$u/"
  if [ -d "/home/$u/.mozilla/" ]; then
    find /home/$u/.mozilla/ -name pluginreg.dat | xargs rm
  fi
  if [ -d "/home/$u/.netscape/" ]; then
    find /home/$u/.netscape/ -name plugin-list | xargs rm
  fi
done
echo

####################
# Verify downloads #
####################
newsflash "Verifying downloads..."
numFiles=$(( ${#verifyList[@]} / 4 ))
for (( i = 0 ; i < $numFiles ; i++ ))
do
  if verifyFile "${verifyList[4*i]}" "${verifyList[4*i+1]}" "${verifyList[4*i+2]}" "${verifyList[4*i+3]}"; then
    echo "Verified: ${verifyList[4*i]}"
  else
    echo "WARNING: Can not verify ${verifyList[4*i]}."
    echo "WARNING: Can not verify ${verifyList[4*i]}." >> $LOGFILE
    echo "If this file is important to you, run this script again later,"
    echo "or download the latest mathbuntu script and try again."
  fi
done
echo

####################################
# Bring compilations to foreground #
####################################
newsflash "Waiting for compiling processes to finish..."
echo "wxMaxima...please be patient"
if [ ! -z "$wxmaximaPid" ]; then
  tail -f /tmp/wxmaximaCompile.log &
  wait $wxmaximaPid
  wxmaximaInstalled=`which wxmaxima`
  if [ ! -z "$wxmaximaInstalled" ]; then
    echo "$wxmaximaCandidateVersion" > "$mathbuntuLocal/wxMaxima/version"
  else
    echo "Installation of wxMaxima failed. :\("
    echo "Failure::Installation of wxMaxima failed. :\(" >> $LOGFILE
  fi
fi
echo "Maxima...please be patient"
if [ ! -z "$maximaPid" ]; then
  tail -f /tmp/maximaCompile.log &
  wait $maximaPid
fi
echo "Octave...please be patient"
if [ ! -z "$octavePid" ]; then
  tail -f /tmp/octaveCompile.log &
  wait $octavePid
fi
echo "Lurch...please be patient"
if [ ! -z "$lurchPid" ]; then
  tail -f /tmp/lurchCompile.log &
  wait $lurchPid
  lurchInstalled=`which lurch`
  if [ ! -z "$lurchInstalled" ]; then
    echo "$lurchCandidateVersion" > "$mathbuntuLocal/lurch/version"
  else
    echo "Installation of Lurch failed. :\("
    echo "Failure::Installation of Lurch failed. :\(" >> $LOGFILE
  fi
fi
echo "Sage...please be patient"
if [ ! -z "$sagePid" ]; then
  tail -f /tmp/sageCompile.log &
  wait $sagePid
fi
echo

#########################
# Remove temporary user #
#########################
deleteTempUser

###################################################
# Output Done message and close LOGFILE with date #
###################################################
echo "Done."
echo
date
date >> $LOGFILE
msg="Done.

Installation is complete. Please press OK as this dialog box may not disappear on its own."
if [ "$AUTOMATIC" == "yes" ]; then
  newsflash "$msg"
else
  newsflash "$msg" notimeout
fi


```

onto this file:
Mathbuntu installer launchpad
which contains:
```
#!/usr/bin/env xdg-open
[Desktop Entry]
Categories=Education;Science;Math;X-Red-Hat-Base;X-Red-Hat-Base-Only;
Comment[en_US]=Drop install script here to install mathematics applications
Comment=Drop install script here to install mathematics applications
Exec=sudo %f 2> $(dirname %k)/.files/mathbuntu.err
GenericName[en_US]=
GenericName=
Icon=libreoffice-math
MimeType=
Name[en_US]=Mathbuntu installer launchpad
Name=Mathbuntu installer launchpad
Path=
StartupNotify=true
Terminal=true
TerminalOptions=
Type=Application
X-DBUS-ServiceName=
X-DBUS-StartupType=none
X-KDE-SubstituteUID=false
X-KDE-Username=


```

and I'm getting this error:
Failed to change to directory '' (No such file or directory)

---

### Post by steeldriver on 2014-07-09
I would suggest just running the installMathUbuntuXX.XX script manually from a terminal 

```

cd Downloads/mathUbuntuXX.XX

chmod +x installMathUbuntuXX.XX

sudo ./installMathUbuntuXX.XX

```

where XX.XX is the release number - modify as appropriate. 

As to why it's not working according to the instructions, that may just be down to differences in how the various file managers handle drag'n'drop - the webpage is pretty specific about using either nautilus (in plain Ubuntu) or dolphin (Kubuntu).

---

### Post by will-earnshaw on 2014-07-09
> **steeldriver said:**
> I would suggest just running the installMathUbuntuXX.XX script manually from a terminal 

```

cd Downloads/mathUbuntuXX.XX

chmod +x installMathUbuntuXX.XX

sudo ./installMathUbuntuXX.XX

```

where XX.XX is the release number - modify as appropriate. 

As to why it's not working according to the instructions, that may just be down to differences in how the various file managers handle drag'n'drop - the webpage is pretty specific about using either nautilus (in plain Ubuntu) or dolphin (Kubuntu).

Awesome! That was the solution, thank you so much!

---

