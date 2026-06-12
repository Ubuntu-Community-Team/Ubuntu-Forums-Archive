---
title: "Convert digiKam keyword tags to Bibble5 / AfterShot Pro XMP-sidecar files"
date: 2012-12-16
forum: General Help
---

### Post by hzFVOW00pw on 2012-12-16
This is an obscure post about Photo Asset Management in the [digiKam Photo Management Application]("http://www.digikam.org") and the [Bibble5/AfterShot Pro RAW Files Convertor and Workflow Application]("http://www.aftershotpro.com"), both very high-class applications.

For a long time I have been waiting for a solution to automagically convert the digiKam keyword database into something that could be used by Bibble5 to create a keyword database. With the release of digiKam 2.0.0, the new Asset Management functions in Bibble5, the support for XMP-sidecar files in both applications, and some oldfashioned Bourne shell programming, it is now possible to convert the digiKam tag keywords for use in Bibble5, while retaining keyword hierarchy.

I successfully converted my digiKam keyword database with the help of a shellscript that I wrote, and I just like to share the proceedings with those two other people in the universe that might be interested in this solution. Note that this solution is primarily intended for seasoned Linux users who know how to run, edit, or even write a Bourne shellscript without wreaking havoc on their system.

**BIG FAT WARNING: YOU SHOULD BACKUP YOUR PHOTO COLLECTION AND EVERYTHING ELSE BEFORE EVEN TRYING TO GO AHEAD WITH THE STEPS DESCRIBED IN THIS TUTORIAL!**

To install digiKam you will have to add the following PPA to your software sources. Run these commands from a Terminal:

```
sudo add-apt-repository ppa:philip5/extra && sudo apt-get update
sudo apt-get install digikam2 kipi-plugins2
```

Or simply add:

```
ppa:philip5/extra
```

to the software sources in the Synaptic Package Manager.

Next, start digiKam, and and from digiKam&#8217;s main window go to **"Settings > Configure digiKam"**, and select the Metadata icon from the left pane. Select **"Save image tags as Keywords tags in metadata embedded in files."** Select **"Metadata Writing Mode: Write to XMP sidecar only"** (No metadata will be written to any images directly but it will write all metadata into a separate XMP file in the same directory as the image.) You can [find some more details here]("http://userbase.kde.org/Digikam/Using_XMP_Sidecar_support_in_digiKam_2").

[ATTACH]228782[/ATTACH]

DO NOT SELECT **"Read metadata from XMP sidecar files"**. This will SYNCHRONISE the metadata in the already existing sidecar files with metadata from the digKam database. This can break your existing sidecar files if you have incompatible XMP files which were created  by another application, and those are not going to work with the conversion script. We need to generate XMP files that are as clean as possible.

XMP files from another application that are already present in your collection will NOT be overwritten by digiKam. I know for sure, because I tested all this personally.

Now close the options window and, then, from the menubar, click on **"Tools > Write Metadata to All Images"** and digiKam will start writing your precious keyword metadata to XMP sidecar files.

After this is done, it is time to run the little convertor shell script that I wrote, copy paste the following code into gedit and save to /path/to/script/photo-d2b-xmp:

```
#!/bin/bash
#
# Description: This script can convert Digikam Keyword Tags to Bibble/AfterShot Pro XMP sidecar files
#
# Usage: Place the script in "/usr/local/bin", do a
#
# "chmod +x /usr/local/bin/photo-d2b-xmp" as root.
#
# Then, copy the script TO THE ROOT OF YOUR IMAGE COLLECTION
#
# cp "/path/to/script/d2bxmp" "/path/to/collectionroot/photo-d2b-xmp"
#
# Change to the location of the script and run it:
#
# cd "/path/to/collectionroot/" && ./photo-db2-xmp
#
# Uncomment for debugging
#
# set -x
#
# Start script

echo -e "\n\033[1;33mSTATUS\033[0m: Script \"$(basename $0)\" started...\n"

find "." -name "*.xmp" | sort -d -r | while read file ; do

    dir="$(dirname ${file})"
    file="$(basename ${file} .xmp)"

    if grep -q "digiKam" ${dir}/${file}.xmp; then

	#keywords="$(cat ${dir}/${file}.xmp | grep "|" | sed "s|.*<rdf:li>||;s|</rdf:li>||;s|\||;|g" | tr '\n' ',')"

	# Fix by Dave Clendenan
	keywords="$(cat ${dir}/${file}.xmp | grep "|" | sed "s|_Digikam_root_tag_\|||;s|.*<rdf:li>||;s|</rdf:li>||;s|\||;|g" | tr '\n' ',')"

	echo "Processing [${file}] - [${keywords}]"

cat > ${dir}/${file}.tmp << EOF
<x:xmpmeta xmlns:x="adobe:ns:meta/" x:xmptk="XMP Core 4.4.0">
 <rdf:RDF xmlns:rdf="http://www.w3.org/1999/02/22-rdf-syntax-ns#">
  <rdf:Description rdf:about=""
    xmlns:dmf="http://www.bibblelabs.com/DigitalMasterFile/1.0/"
    xmlns:dmfversion="http://www.bibblelabs.com/DigitalMasterFileVersion/1.0/"
    xmlns:bset="http://www.bibblelabs.com/BibbleSettings/5.0/"
    xmlns:blay="http://www.bibblelabs.com/BibbleLayers/5.0/"
    xmlns:bopt="http://www.bibblelabs.com/BibbleOpt/5.0/"
   dmf:versionCount="1">
   <dmf:versions>
    <rdf:Seq>
     <rdf:li>
      <rdf:Description
       dmfversion:software="bibble"
       dmfversion:softwareVersion="2008.1"
       dmfversion:versionName="${file}">
      <dmfversion:settings>
       <rdf:Description
        bset:settingsVersion="66"
        bset:respectsTransform="True"
        bset:curLayer="0">
       <bset:layers>
        <rdf:Seq>
         <rdf:li>
          <rdf:Description
           blay:layerId="0"
           blay:layerPos="0"
           blay:name=""
           blay:enabled="True">
          <blay:options
           bopt:keywordlist="${keywords}"/>
          </rdf:Description>
         </rdf:li>
        </rdf:Seq>
       </bset:layers>
       </rdf:Description>
      </dmfversion:settings>
      </rdf:Description>
     </rdf:li>
    </rdf:Seq>
   </dmf:versions>
  </rdf:Description>
 </rdf:RDF>
</x:xmpmeta>
EOF

	mv ${dir}/${file}.tmp ${dir}/${file}.xmp

	unset keywords

    fi

done

echo "Done... Hit enter to quit..."

read

exit 0
```

Open a Terminal and change the file permissions to make it executable:

```
chmod ugo+x "/path/to/script/photo-d2b-xmp"
```

Copy the script **TO THE ROOT OF YOUR IMAGE COLLECTION**.

```
cp "/path/to/script/d2bxmp" "/path/to/collectionroot/photo-d2b-xmp"
```

Change to the location of the script and run it:

```
cd "/path/to/collectionroot/" &amp;&amp; ./photo-db2-xmp
```

Of course you can also accomplish these tasks from any file manager like Nautilus, Dolphin or Thunar to make life more easy.

After the script is done you will have Bibble5 sidecar files in your collection folders, and Bibble5 will read the tags/keywords from these files. You can create collections in Bibble5 and you will have a keyword hierarchy.

**DISASTER RECOVERY:**

I have tested all this with Canon CR2/CRW RAW files and some JPG files from an old Olympus camera. It worked really well for me, but of course there might be a possibility that it won't work with other camera brands/files. If you mess things up, and if Bibble5 crashes on the newly created XMP files you can remove these new files by opening a Terminal and changing to the root of your image collection, and then run the following command (You can copy paste the complicated command line in the Terminal for convenience):

Change to the location of your image collection:

```
cd "/path/to/collectionroot/"
```

Run this command to remove the offending miscreant XMP files:

```
find "." -name "*.xmp" | sort -d -r | while read file; do if grep -q "digiKam" ${file}; then rm -fv ${file}; fi done
```

Now, if you REALLY messed things up by accidentally SYNCHRONISING  the digiKam XMP files with files from another application (yes, I had to learn it the hard way), you can remove the files with this command:

```
find "." -name "*.xmp" | sort -d -r | while read file; do if grep -q "digiKam" ${file} | grep -q "keywordlist" ${file}; then rm -fv ${file}; fi done
```

But be aware that this last command will also remove valid Bibble5 XMP files which already contain keywords. So if you were already using a keyword hierarchy in Bibble5 you really do NOT want to run this last command.

If you want to know beforehand which files these commands will remove, simply replace "rm -fv" by "echo", and optionally log the output to a text file, like in this example:

```
find "." -name "*.xmp" | sort -d -r | while read file; do if grep -q "digiKam" ${file} | grep -q "keywordlist" ${file}; then echo ${file}; fi done > logfile.txt
```

Open logfile.txt with any text editor, for scrutinization.

Have a nice day.

---

