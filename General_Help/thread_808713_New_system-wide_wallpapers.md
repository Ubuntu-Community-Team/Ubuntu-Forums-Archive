---
title: "New system-wide wallpapers"
date: 2008-05-26
forum: General Help
---

### Post by mmerlone on 2008-05-26
Hello,

Sorry if this has been answered before, but if you google for gnome desktop wallpaper you get flooded with zillions of links.

I have some pics I want to make available to all users on my system, I cp them to /usr/share/backgrounds and they did not show up on the change background dialog.

I know how to add one new background wallpaper, either via browser right-click and via gnome desktop right-click. But now I want to know how to add a bunch of pics at once in such a way they will be available to all users.

Thanks for any help. Best regards.

---

### Post by ShodanjoDM on 2008-05-26
Do you have an .xml file inside /usr/share/backgrounds/ ?

If yes, you can see that it contains the default wallpaper filenames that accessible to all users. Try adding new ones in it.

Although this one is maybe unecessary, but I do feel it's a good practice to change the ownership and permission of the additional wallpapers as the same as the default ones.

---

### Post by mmerlone on 2008-05-26
> **ShodanjoDM said:**
> Do you have an .xml file inside /usr/share/backgrounds/ ?

No.


> **ShodanjoDM said:**
> Although this one is maybe unecessary, but I do feel it's a good practice to change the ownership and permission of the additional wallpapers as the same as the default ones.

Indeed. I agree and did it already. But still no new backgrounds on gnome change desktop background applet.

---

### Post by ShodanjoDM on 2008-05-26
Ok, I copied the ubuntustudio-wallpapers.xml.in file from my ubuntustudio's /usr/share/backgrounds and attached it below.

Here's the default content:

> <?xml version="1.0"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>

  <wallpaper>
    <_name>Ubuntu Studio Default</_name>
    <filename>/usr/share/backgrounds/ubuntustudio.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

  <wallpaper>
    <_name>Ubuntu Studio Gutsy </_name>
    <filename>/usr/share/backgrounds/ubuntustudio-gutsy.png</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

  <wallpaper>
    <_name>Ubuntu Studio Ayo</_name>
    <filename>/usr/share/backgrounds/ubuntustudio-ayo.png</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

  <wallpaper>
    <_name>Ubuntu Studio Graphics </_name>
    <filename>/usr/share/backgrounds/ubuntustudio-brushes.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

  <wallpaper>
    <_name>Ubuntu Studio Video </_name>
    <filename>/usr/share/backgrounds/ubuntustudio-lense.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

</wallpapers>

---

### Post by mmerlone on 2008-05-26
> **ShodanjoDM said:**
> Ok, I copied the ubuntustudio-wallpapers.xml.in file from my ubuntustudio's /usr/share/backgrounds and attached it below.

Cool, many thanks! Edited the file and created the one attached. But still, no luch, no new wallpapers on "Change desktop background" dialog.
("Change desktop background" is my translation for "Alterar Plano de Fundo", wich is Brazilian portuguese pt_BR. May be different on en_US. Just to let you know).

---

### Post by ShodanjoDM on 2008-05-26
Oops, my bad. Should've told you before that the file serves as an example - including the filename. It should works if you change the filename to "ubuntu-wallpapers.xml.in" or "hardy-wallpapers.xml.in".

This is where I've got the idea from:

[https://code.launchpad.net/~ubuntu-art-pkg/gutsy-wallpapers/ubuntu](https://code.launchpad.net/~ubuntu-art-pkg/gutsy-wallpapers/ubuntu)

---

### Post by wzf851005 on 2008-05-27
These patterns are based on different foot type, weight, Speed, training programmes, gender and skill level design. These different styles, different prices and multi-purpose products, attracting hundreds of thousands of jogging, making them feel that [nike shoes](http://www.bestbuynike.com) is to provide the most complete variety of running shoes manufacturers, millions of range of ability Running to have that belief.   First-generation jordan shoes uppers, there is a conspicuous "Chachi basketball" signs in the use of trapeze signs ago, the first generation and second generation Chachi Jordan basketball shoes are used as signs. First-generation[jordan shoes](http://www.pickyourjordan.com) appeared in 1985, 1994 and 2001 NIKE companies produced twice again this shoes. For the classic colors with a red, black, and compared with black. [Air Jordans](http://www.oknike.com), published in 1991, jordan shoes91-92 season Zhanxue because jordan shoesin the Barcelona Olympic Games 92 wearing this pair of 7 and winning the title, the seventh generation in jordan shoesin the series, it is particularly valuable. 7 and the shape of the shadow of some six generations, the biggest feature is particularly color.  Borrow a relatives [chinese dress](http://www.prettyladygirl.com/). Sometimes those old chinese dresses are outdated beyond repair, but then again, sometimes theyre not. If you have an (aunt, mom, cousin, sister) who got married in a strapless sheath that would be perfect, theres no reason you couldnt too, assuming theyre open to loaning it out. You can still make the look your own with the veil, jewelry, shoes, a pretty sash. And youll have that &#8220;something borrowed&#8221; checked off the list.What about the modern cheongsam? With more exchange with the outside world, todays [cheongsam](http://www.prettyladygirl.com/) combines both Chinese and western characteristics, traditional and modern features. There are bold changes and innovations. Whatever it is, cheongsam on one hand can still create an impression of simple and quite charm, elegance and neatness. On the other hand, blended with modern features, they can also show peoples individuality and distinctiveness. No wonder cheongsam enjoys a growing popularity in the international world of high fashion.

---

### Post by mmerlone on 2008-05-27
> **ShodanjoDM said:**
> It should works if you change the filename to "ubuntu-wallpapers.xml.in" or "hardy-wallpapers.xml.in".

Tried both. No luck...

---

### Post by daemon_cleaner on 2008-09-27
Gnome is looking for background.xml-files in /usr/share/gnome-background-properties/ and /usr/local/share/gnome-background-properties/. I don't know why you can't just drop your pictures to /usr/share/backgrounds/ to make them available system-wide like fonts, icons, sounds or anything else. It's a stupid idea, IMHO, to manage wallpapers through xml-files that are not updated/created for example on sessions startup trough just listing picture-files in pictures-directories.(Even on some dumb OS's you can just put pictures to wallpapers-directory and make them available systemwide that way). 

What you can do is: 
- edit the right xml-files (in /usr/share/gnome-background-properties/) 
- just rename your wallpapers to the default ubuntu-wallpaper-names (replace ubuntu ones)
- Find a solution here:
[http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide]("http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide")      

It would take still a long time to edit backgrounds.xml if you want to make, lets say, all your 100 pictures in (for example) /home/$USER/Pictures/ available as wallpapers for all users. That's why I've created a script to create mybackground.xml-files. It works for me on hardy. It would be possible to execute it on startup. Take a look at how it works:
 
```
#!/bin/bash
clear
echo "#################################"
echo "This script makes all pictures in selected custom directory"
echo "available as your system-wide GNOME wallpapers." 
# It reads/lists all pictures in selected directory and creates mybackgrounds.xml file in /usr/local/share/gnome-background-properties/. USAGE: Make this script executable (chmod +x backgrounds.sh) and execute it (sudo ./backgrounds.sh or ./backgrounds.sh as root)." 
echo "#################################"
echo
# if doesn't exists creating directory /usr/local/share/gnome-background-properties
mkdir -p /usr/local/share/gnome-background-properties
echo "Enter the path to your pictures directory"
echo \(\for example\: \/home\/myname\/Pictures\/\) 
echo "Don't forget the slash at the end of pathname!"
echo -n "$"
read DIRECTORY
echo
if [ ! -d $DIRECTORY ]
then
    echo "Sorry, you entered wrong path."
    echo "Directory $DIRECTORY doesnot exists"
    echo "You have to start the Script again."	
    exit
fi
echo "You selected $DIRECTORY:"
ls $DIRECTORY > lspictures.txt
cat lspictures.txt
echo
# creating the head of mybackgrounds.xml
echo "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE wallpapers SYSTEM \"gnome-wp-list.dtd\">
<wallpapers>" > mybackgrounds.xml
# looking for all pictures in $DIRECTORY
echo "OK. Now we are creating mybackgrounds.xml"
# This script is looking for .png and .jpg files only, but you can add here another file types. The "<options>stretched</options>" should work best for unknow sized files.
for i in $DIRECTORY*.jpg $DIRECTORY*.png; do
echo "<wallpaper>
<name>$i</name>
<filename>$i</filename>
  <options>stretched</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>" >> mybackgrounds.xml
done
# creating the bottom of mybackgrounds.xml
echo "</wallpapers>" >> mybackgrounds.xml
# Change <name>/path_to/picture</name> to <name>picture</name> and move mybackgrounds.xml  to /usr/local/share/gnome-background-properties/.
sed 's/<name>\/usr\/share\/backgrounds\//<name>/g' mybackgrounds.xml > /usr/local/share/gnome-background-properties/mybackgrounds.xml
# if you like to copy mybackgrounds.xml to /usr/share/gnome-background-properties/mybackgrounds.xml as well
cp /usr/local/share/gnome-background-properties/mybackgrounds.xml /usr/share/gnome-background-properties/mybackgrounds.xml
# clear now
rm mybackgrounds.xml
rm lspictures.txt
echo
echo "#################################"
echo "You're almost done. Log out and back in. Invoke the Desktop"
echo "Background Change application again, and all your selected" 
echo "wallpapers should be available."
echo "#################################"
echo
exit 0
```

---

### Post by wilbertnl on 2009-05-07
> **daemon_cleaner said:**
> I don't know why you can't just drop your pictures to /usr/share/backgrounds/ to make them available system-wide like fonts, icons, sounds or anything else. It's a stupid idea, IMHO, to manage wallpapers through xml-files that are not updated/created for example on sessions startup trough just listing picture-files in pictures-directories.(Even on some dumb OS's you can just put pictures to wallpapers-directory and make them available systemwide that way). 

This is what I tried:
On my desktop I create a folder with all my custom jpg files.
In Appearance Preference I open the Wallpaper tab and select 'Add', then I browse to my folder and select all files.
These files are then available in the background tab.
In you ~/.gnome2/ folder you will find a brand new backgrounds.xml file with all the references to your custom pictures.

My guess is that you can do the same with pictures from /usr/share/backgrounds/<any subfolder> and you would copy the generated xml file (in ~/.gnome2) to /usr/share/gnome-background-properties/ubuntu-wallpapers.xml?

**# cat ~/.gnome2/backgrounds.xml > /usr/share/gnome-background-properties/ubuntu-wallpapers.xml** did work for me!

---

### Post by clivelr on 2009-09-29
> **daemon_cleaner said:**
> Gnome is looking for background.xml-files in /usr/share/gnome-background-properties/ and /usr/local/share/gnome-background-properties/. I don't know why you can't just drop your pictures to /usr/share/backgrounds/ to make them available system-wide like fonts, icons, sounds or anything else. It's a stupid idea, IMHO, to manage wallpapers through xml-files that are not updated/created for example on sessions startup trough just listing picture-files in pictures-directories.(Even on some dumb OS's you can just put pictures to wallpapers-directory and make them available systemwide that way). 

What you can do is: 
- edit the right xml-files (in /usr/share/gnome-background-properties/) 
- just rename your wallpapers to the default ubuntu-wallpaper-names (replace ubuntu ones)
- Find a solution here:
[http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide]("http://linux.wikia.com/wiki/How_To_make_your_GNOME_desktop_wallpapers_available_system-wide")      

It would take still a long time to edit backgrounds.xml if you want to make, lets say, all your 100 pictures in (for example) /home/$USER/Pictures/ available as wallpapers for all users. That's why I've created a script to create mybackground.xml-files. It works for me on hardy. It would be possible to execute it on startup. Take a look at how it works:
 
```
#!/bin/bash
clear
echo "#################################"
echo "This script makes all pictures in selected custom directory"
echo "available as your system-wide GNOME wallpapers." 
# It reads/lists all pictures in selected directory and creates mybackgrounds.xml file in /usr/local/share/gnome-background-properties/. USAGE: Make this script executable (chmod +x backgrounds.sh) and execute it (sudo ./backgrounds.sh or ./backgrounds.sh as root)." 
echo "#################################"
echo
# if doesn't exists creating directory /usr/local/share/gnome-background-properties
mkdir -p /usr/local/share/gnome-background-properties
echo "Enter the path to your pictures directory"
echo \(\for example\: \/home\/myname\/Pictures\/\) 
echo "Don't forget the slash at the end of pathname!"
echo -n "$"
read DIRECTORY
echo
if [ ! -d $DIRECTORY ]
then
    echo "Sorry, you entered wrong path."
    echo "Directory $DIRECTORY doesnot exists"
    echo "You have to start the Script again."	
    exit
fi
echo "You selected $DIRECTORY:"
ls $DIRECTORY > lspictures.txt
cat lspictures.txt
echo
# creating the head of mybackgrounds.xml
echo "<?xml version=\"1.0\" encoding=\"UTF-8\"?>
<!DOCTYPE wallpapers SYSTEM \"gnome-wp-list.dtd\">
<wallpapers>" > mybackgrounds.xml
# looking for all pictures in $DIRECTORY
echo "OK. Now we are creating mybackgrounds.xml"
# This script is looking for .png and .jpg files only, but you can add here another file types. The "<options>stretched</options>" should work best for unknow sized files.
for i in $DIRECTORY*.jpg $DIRECTORY*.png; do
echo "<wallpaper>
<name>$i</name>
<filename>$i</filename>
  <options>stretched</options>
    <pcolor>#8f4a1c</pcolor>
    <scolor>#8f4a1c</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>" >> mybackgrounds.xml
done
# creating the bottom of mybackgrounds.xml
echo "</wallpapers>" >> mybackgrounds.xml
# Change <name>/path_to/picture</name> to <name>picture</name> and move mybackgrounds.xml  to /usr/local/share/gnome-background-properties/.
sed 's/<name>\/usr\/share\/backgrounds\//<name>/g' mybackgrounds.xml > /usr/local/share/gnome-background-properties/mybackgrounds.xml
# if you like to copy mybackgrounds.xml to /usr/share/gnome-background-properties/mybackgrounds.xml as well
cp /usr/local/share/gnome-background-properties/mybackgrounds.xml /usr/share/gnome-background-properties/mybackgrounds.xml
# clear now
rm mybackgrounds.xml
rm lspictures.txt
echo
echo "#################################"
echo "You're almost done. Log out and back in. Invoke the Desktop"
echo "Background Change application again, and all your selected" 
echo "wallpapers should be available."
echo "#################################"
echo
exit 0
```


Hey daemon_cleaner,

Your script almost worked for me on jaunty, but it did not handle files with spaces in their names. 

I have modified your script to handle them correctly, it uses 3 variables at the beginning of the file which is all anyone should need to change to get working on their own system. This way it can be run as a daily cron job for example, and would not need user-intervention.

Cheers
Clive

Modified Code follows:
```
#!/bin/bash
#
# This script will take all wallpapers in $WALLPAPER_DIR and
# make them available as "default" background in the "Change Background" gui
# frontend in Ubuntu.
#
# Basically what it does is create an xml file in the
# /usr/share/gnome-background-properties directory which is read whenever a
# user logs into the system.
#
# All that should need changing to work in any other user's system is:
# WALLPAPER_DIR  (line 15)
# XML_FILE       (line 17)
################################################################################
WALLPAPER_DIR="/usr/local/share/wallpapers"
CONFIG_DIR="/usr/share/gnome-background-properties"
XML_FILE="$CONFIG_DIR/shared-wallpapers.xml"

#### First check if we have write permissions to the share dirctory. ####
touch $CONFIG_DIR/testfile >/dev/null 2>/dev/null
if [[ $? -ne 0 ]]; then
   echo "**** No permissions to the desktop share directory. ****"
   echo "**** $CONFIG_DIR ****"
   echo "**** Procedure Terminated. ****"
   exit 1
else
   rm $CONFIG_DIR/testfile 2>/dev/null
fi

#### Show the script description message. ###
cat <<EOF

################################################################################
     This script makes all pictures in the $WALLPAPER_DIR
     directory available to all users defined on this system as their
     system-wide GNOME wallpapers.

     This script should be run as "root" or with "sudo".
     e.g. sudo $0
################################################################################
EOF

#### Fail if the wallpaper directory does not exist. ####
if [[ ! -d $WALLPAPER_DIR ]]; then
    echo "**** The wallpaper directory \"$WALLPAPER_DIR\" does not exist. ****"
    echo "**** Precedure Terminated. ****"
    exit 1
fi

#### Count the number of jpg/jpeg/png images. ####
numfiles=`ls -1 $WALLPAPER_DIR/*.jpg WALLPAPER_DIR/*.jpeg WALLPAPER_DIR/*.png 2>/dev/null | wc -l`

#### If there are no image files there then exit. ####
if [[ $numfiles -eq 0 ]]; then
    echo "**** The wallpaper directory \"$WALLPAPER_DIR\" has no images. ****"
    echo "**** Precedure Terminated. ****"
    exit 1
fi

#### Now we create the XML file containing the images for backgrounds. ####
#### Start by creating the header in the XML file. ####
cat <<EOF > $XML_FILE
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
EOF

#### Add each file to the XML file. ####
#### Doing it this way makes sure files with spaces in their names are ####
#### handled properly.   (ls .... | while read fname; do)              ####
ls -1 $WALLPAPER_DIR/*.jpg $WALLPAPER_DIR/*.png $WALLPAPER_DIR/*.jpeg 2> /dev/null |
while read image_name; do
   echo "   Adding: `basename "$image_name"`."
   fname=`basename "$image_name"`
   fname="${fname%%\.*}"
   echo "  <wallpaper>"                          >> $XML_FILE
   echo "    <name>$fname</name>"                >> $XML_FILE
   echo "    <filename>$image_name</filename>"   >> $XML_FILE
   echo "    <options>stretched</options>"       >> $XML_FILE
   echo "    <pcolor>#c58357</pcolor>"           >> $XML_FILE
   echo "    <scolor>#c58357</scolor>"           >> $XML_FILE
   echo "    <shade_type>solid</shade_type>"     >> $XML_FILE
   echo "  </wallpaper>"                         >> $XML_FILE
done

#### Create the footer for the XML file. ####
echo "</wallpapers>"                             >> $XML_FILE

#### Lastly display a message to inform caller to logout and back in. ####
cat <<EOF
################################################################################
     You're almost done. Log out and back in. Invoke the Desktop Background
     Change application again, and all your selected wallpapers should be
     available to use for all users.
################################################################################

EOF
```

---

### Post by Gramathur on 2012-05-25
***Daemon_cleaner*** and ***Clivelr***,

 I made a modification to the script Clivelr, adding the request of the User directory entry, as Daemon_cleaner was placed.

 This way the script worked and allowed us to fully customize the User directory.

 This is my contribution to you. And very grateful to both.

 Here I made the change:

```


#!/bin/bash
#
# This script will take all wallpapers in $WALLPAPER_DIR and
# make them available as "default" background in the "Change Background" gui
# frontend in Ubuntu.
#
# Basically what it does is create an xml file in the
# /usr/share/gnome-background-properties directory which is read whenever a
# user logs into the system.
#
# All that should need changing to work in any other user's system is:
# WALLPAPER_DIR  (line 15)
# XML_FILE       (line 17)
################################################################################
mkdir -p /usr/local/share/gnome-background-properties
echo "Enter the path to your pictures directory"
echo \(\for example\: \/home\/myname\/Pictures\/\) 
## echo "Don't forget the slash at the end of pathname!" (Note: It is not necessary because the code Clivelr resolve this issue later in the script.)
echo -n "$"
read WALLPAPER_DIR
echo
if [ ! -d $WALLPAPER_DIR ]
then
    echo "Sorry, you entered wrong path."
    echo "Directory $WALLPAPER_DIR doesnot exists"
    echo "You have to start the Script again."    
    exit
fi
echo "You selected $WALLPAPER_DIR:"

## WALLPAPER_DIR="/usr/local/share/wallpapers" (Note: Taken to the user himself put the directory that he wants, according to the original code of the Daemon_cleaner.)
CONFIG_DIR="/usr/share/gnome-background-properties"
XML_FILE="$CONFIG_DIR/shared-wallpapers.xml"

#### First check if we have write permissions to the share dirctory. ####
touch $CONFIG_DIR/testfile >/dev/null 2>/dev/null
if [[ $? -ne 0 ]]; then
   echo "**** No permissions to the desktop share directory. ****"
   echo "**** $CONFIG_DIR ****"
   echo "**** Procedure Terminated. ****"
   exit 1
else
   rm $CONFIG_DIR/testfile 2>/dev/null
fi

#### Show the script description message. ###
cat <<EOF

################################################################################
     This script makes all pictures in the $WALLPAPER_DIR
     directory available to all users defined on this system as their
     system-wide GNOME wallpapers.

     This script should be run as "root" or with "sudo".
     e.g. sudo $0
################################################################################
EOF

#### Fail if the wallpaper directory does not exist. ####
if [[ ! -d $WALLPAPER_DIR ]]; then
    echo "**** The wallpaper directory \"$WALLPAPER_DIR\" does not exist. ****"
    echo "**** Precedure Terminated. ****"
    exit 1
fi

#### Count the number of jpg/jpeg/png images. ####
numfiles=`ls -1 $WALLPAPER_DIR/*.jpg WALLPAPER_DIR/*.jpeg WALLPAPER_DIR/*.png 2>/dev/null | wc -l`

#### If there are no image files there then exit. ####
if [[ $numfiles -eq 0 ]]; then
    echo "**** The wallpaper directory \"$WALLPAPER_DIR\" has no images. ****"
    echo "**** Precedure Terminated. ****"
    exit 1
fi

#### Now we create the XML file containing the images for backgrounds. ####
#### Start by creating the header in the XML file. ####
cat <<EOF > $XML_FILE
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE wallpapers SYSTEM "gnome-wp-list.dtd">
<wallpapers>
EOF

#### Add each file to the XML file. ####
#### Doing it this way makes sure files with spaces in their names are ####
#### handled properly.   (ls .... | while read fname; do)              ####
ls -1 $WALLPAPER_DIR/*.jpg $WALLPAPER_DIR/*.png $WALLPAPER_DIR/*.jpeg 2> /dev/null |
while read image_name; do
   echo "   Adding: `basename "$image_name"`."
   fname=`basename "$image_name"`
   fname="${fname%%\.*}"
   echo "  <wallpaper>"                          >> $XML_FILE
   echo "    <name>$fname</name>"                >> $XML_FILE
   echo "    <filename>$image_name</filename>"   >> $XML_FILE
   echo "    <options>zoom</options>"            >> $XML_FILE
   echo "    <pcolor>#000000</pcolor>"           >> $XML_FILE
   echo "    <scolor>#000000</scolor>"           >> $XML_FILE
   echo "    <shade_type>solid</shade_type>"     >> $XML_FILE
   echo "  </wallpaper>"                         >> $XML_FILE
done

#### Create the footer for the XML file. ####
echo "</wallpapers>"                             >> $XML_FILE

#### Lastly display a message to inform caller to logout and back in. ####
cat <<EOF
################################################################################
     You're almost done. Log out and back in. Invoke the Desktop Background
     Change application again, and all your selected wallpapers should be
     available to use for all users.
################################################################################

EOF


```

---

### Post by oldos2er on 2012-05-25
Old thread closed.

---

