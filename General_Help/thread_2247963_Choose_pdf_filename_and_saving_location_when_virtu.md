---
title: "Choose pdf filename and saving location when virtual printing to pdf-printer ?"
date: 2014-10-11
forum: General Help
---

### Post by Cbhihe on 2014-10-11
When sending a job to a virtual printer to make a pdf file, the CUPS' or CUPS-PDF's default seems to be [FONT=courier new]~/PDF/[/FONT] for the folder and the first sentence or at least a piece of it, if it is a unnamed file or an html page such as the one you are reading now.

Is there a way to tweak cups and/or cups-pdf in  order to be able to choose the generated file's name and default folder  where the pdf file is saved, as in the typical "Save As" app's gui behavior ?

  Background: Just installed cups-pdf v2.6.1-9 to be able to virtual-print in the form of a pdf file. Everything works fine except for the fact that default settings are a pain in the neck  :mad:.
      

* [This is cross-posting from askubuntu.com, where my post received exactly zilch answer or comment, more than 3 days ago. Don't know why ...]*

---

### Post by nerdtron on 2014-10-11
Nor using cupspdf at the moment, but according to the docs, do you have the file /etc/cups/cups-pdf.conf?
If so, can you post the contents here, I believe the default location of save folder is defined there.

Edit: I re-read your post and I don't think there is a "save-as" option in cups-pdf. Anyway, if your document is in OpenOffice/LibreOffice there is an option to save as PDF.

---

### Post by Cbhihe on 2014-10-11
Inspecting the [FONT=courier new]/etc/cups/cups-pdf.conf[/FONT] file, two spots should permit tweaking default save directory and filename choice by user:   
- the [FONT=courier new]Out[/FONT] key to define the default folder,
and I guess   
- the [FONT=courier new]TitlePref[/FONT] key to allow specifying the file name on-the-fly by the user.  

The problem is neither of them worked as duly commented in the file below. The only "Save" directory acceptable to cups-pdf seems to be[FONT=courier new] ~/PDF[/FONT] and setting the [FONT=courier new]TitlePref[/FONT] to 1 causes 0 file to be saved.

  [B]Does anybody out there know how to proceed ?

[/B]```
#  cups-pdf.conf -- CUPS Backend Configuration (version 2.6.1, 2011-10-04)


# Path Settings

### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}
Out ${HOME}/PDF
#Out ${HOME}/Desktop/Downloads -> nothing but ${HOME}/PDF seems to work

### Key: AnonDirName
##  ABSOLUTE path for anonymously created PDF files
##  if anonymous access is disabled this setting has no effect
### Default: /var/spool/cups-pdf/ANONYMOUS
#AnonDirName /var/spool/cups-pdf/ANONYMOUS

### Key: Spool
##  CUPS-PDF spool directory - make sure there is no user 'SPOOL' on your
##  system or change the path   
### Default: /var/spool/cups-pdf/SPOOL
#Spool /var/spool/cups-pdf/SPOOL


# Filename Settings

### Key: Truncate
##  truncate long filenames to a maximum of <Truncate> characters
##  this does not consider the full path to the output but only the filename
##  without the .pdf-extension or a job-id prefix (see 'Label')
##  the minimal value is 8
### Default: 64
#Truncate 64

### Key: Cut
##  removing file name extensions before appending .pdf to output
##  extensions will only be removed if _both_ the following criteria are met:
##   - the extension (w/o the dot) is not longer than <Cut> characters
##   - the remaining filename has a minimal length of 1 character
##  set Cut to -1 in order to disable cutting
##  recommended values: pure UNIX environment : -1
##                      mixed environments    :  3
### Default: 3
#Cut 3

### Key: Label
##  label all jobs with a unique job-id in order to avoid overwriting old
##  files in case new ones with identical names are created; always true for
##  untitled documents
##  0: label untitled documents only
##  1: label all documents with a preceeding "job_#-"
##  2: label all documents with a tailing "-job_#"
### Default: 0
#Label 0

### Key: TitlePref
##  where to look first for a title when creating the output filename
##  (title in PS file or title on commandline):
##  0: prefer title from %Title statement in the PS file
##  1: prefer title passed via commandline 
### Default: 0
#TitlePref 1  
# changed to 1 on 2014.10.10 -> no filename generated

# User Settings

### Key: AnonUser
##  uid for anonymous PDF creation (this might be a security issue)
##  this setting has no influence on AnonDirName (see there)
##  set this to an empty value to disable anonymous
### Default: nobody
#AnonUser nobody

### Key: LowerCase
##  This options allows to check user names given to CUPS-PDF additionally 
##  against their lower case variants. This is necessary since in some 
##  Windows environments only upper case user names are passed. Usually UNIX
##  user names are all lower case and it is save to use this option  
##  but be aware that it can lead to mis-identifications in case
##  you have user names that differ only in upper/lower case.
##     check only against user name as passed to CUPS  : 0
##     check additionally against lower case user name : 1
### Default: 1
#LowerCase 1

### Key: UserPrefix
##  some installations require a domain prefix added to the user name
##  leave empty for no prefix 
### Default: <empty>
#UserPrefix

### Key: DirPrefix
##  if a prefix was defined above this switch toggels whether to include
##  the prefix in the output directory's name (if not $HOME) or not
##  0: do not include, 1: include
### Default: 0
#DirPrefix 0

### Key: RemovePrefix
##  some installation pass usernames with a prefix (usually a domain name)
##  if you do not want this prefix to be used by the ${USER} variable for
##  output directories put the part which is to be cut here
### Default: <empty>
#RemovePrefix


# Security Settings

### Key: AnonUMask
##  umask for anonymous output
##  these are the _inverse_ permissions to be granted
### Default: 0000
#AnonUMask 0000

### Key: UserUMask
##  umask for user output of known users
##  changing this can introduce security leaks if confidential
##  information is processed!
### Default: 0077
#UserUMask 0077

### Key: Grp
##  group cups-pdf is supposed to run as - this will also be the gid for all
##  created directories and log files
### Default: lp
Grp lpadmin


# Log Settings

### Key: Log
##  CUPS-PDF log directory 
##  set this to an empty value to disable all logging
### Default: /var/log/cups
Log /var/log/cups

### Key: LogType
##  log-mode 
##  1: errors
##  2: status (i.e. activity)
##  4: debug - this will generate a lot of log-output!
##  add up values to combine options, i.e. 7 is full logging
##  if logging is disabled these setting have no effect
### Default: 3
#LogType 3


# PDF Conversion Settings

### Key: GhostScript
##  location of GhostScript binary (gs) 
##  MacOSX: for using pstopdf (recommended) set this to /usr/bin/pstopdf
##          or its proper location on your system
### Default: /usr/bin/gs
#GhostScript /usr/bin/gs

### Key: GSTmp
##  location of temporary files during GhostScript operation 
##  this must be user-writable like /var/tmp or /tmp ! 
### Default: /var/tmp
#GSTmp /var/tmp

### Key: GSCall
## command line for calling GhostScript (!!! DO NOT USE NEWLINES !!!)
## MacOSX: for using pstopdf set this to %s %s -o %s %s
### Default: %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s
#GSCall %s -q -dCompatibilityLevel=%s -dNOPAUSE -dBATCH -dSAFER -sDEVICE=pdfwrite -sOutputFile="%s" -dAutoRotatePages=/PageByPage -dAutoFilterColorImages=false -dColorImageFilter=/FlateEncode -dPDFSETTINGS=/prepress -c .setpdfwrite -f %s

### Key: PDFVer
##  PDF version to be created - can be "1.5", "1.4", "1.3" or "1.2" 
##  MacOSX: for using pstopdf set this to an empty value
### Default: 1.4
#PDFVer 1.4

### Key: PostProcessing
##  postprocessing script that will be called after the creation of the PDF
##  as arguments the filename of the PDF, the username as determined by 
##  CUPS-PDF and the one as given to CUPS-PDF will be passed
##  the script will be called with user privileges
##  set this to an empty value to use no postprocessing
### Default: <empty>
#PostProcessing 


# Experimental Settings
# These settings activate experimental options. If you decide to use  them I would appreciate any
# feedback - including an 'ok' if they work as expected - so I can eventually put them into the non-
# experimental sections.

### Key: DecodeHexStrings
##  this option will try to decode hex strings in the title to allow internationalized titles
##  (have a look at contrib/pstitleconv for a suitable filter for data from Windows clients)
##  0: disable, 1: enable
### Default: 0
DecodeHexStrings 1

### Key: FixNewlines
##  this option will try to fix various unusal line delimiters (e.g. form feeds)
##  especially useful when using non-Linux-generated files
##  0: disable, 1: enable
### Default: 0
# FixNewlines 0
```

---

### Post by Cbhihe on 2014-10-15
Really ? Nobody knows where to go from there ?

---

### Post by nerdtron on 2014-10-15
Hmm hot sure on the filename but it seems you need to edit the lower variables on the User Settings section too. Also, I hope your Out folder exists, and did you reboot your computer after you made the changes....I don't know what's next if these don't work.

---

### Post by Cbhihe on 2014-10-16
Yup. No clue either. Nothing seems to work. Restarting or not, even though the [FONT=courier new]/etc/cups/cups-pdf.conf[/FONT] file says explicitly:
> # This is the configuration file for CUPS-PDF. Values that are not set in #
# here will use the defaults. Changes take effect immediately without the #
# need for restarting any services. #
I will get in touch with the developer and will report here as things move forward.
Cheers,
-ced

---

### Post by Cbhihe on 2014-10-17
[FONT=arial]Got a nice private mail reply from Volker B., developper cited in[/FONT] [FONT=arial]the header of [/FONT][FONT=courier new]/etc/cups/cups-pdf.conf. [FONT=arial]

The options to choose the destination folder and/or the name of the newly created pdf file were operational at one point. However apparently Ubuntu devs have made changes that invalidated part of the configurability of cups-pdf.
There is no definite timetable for a new implementation, even though it is in the pipeline.

Interestingly, from the terminal, one can specify the pdf file name without a problem:
```
> lp -t test-filename -d *your-pdf-printer-name* ~/.bashrc 
request id is *your-pdf-printer-name*-79 (1 file(s))
> ls -AF ~/PDF
test-filename
```Volker pointed at the possibility to "**automatically post-process**" the result pdf file placed in *${HOME}/PDF*, by use of an ad-hoc script, declared with the *PostProcessing* key listed almost at the end of the conf file.

 I have not experimented with that as of yet, but I will at some point. 

There are two possibilities:

[LIST]
[*] - Terminal post-processing 
[/LIST]
[INDENT]i) Rename file
ii) Move renamed file to arbitrary directory, respecting permissions
[/INDENT]

[LIST]
[*]- GUI post-processing 
[/LIST]
[INDENT]Open a window where the user can rename the file in *${HOME}/PDF* and browse the tree to select a new destination directory.
[/INDENT]

The only two variables passed on to the post-processing scripts are *${USER}* and the pdf [FONT=courier new][FONT=arial]filename, for which I have no defined *${XYZ}* parameter.
[/FONT][/FONT][/FONT] [/FONT]

---

### Post by bab1 on 2014-10-17
> **Cbhihe said:**
> [FONT=arial]Got a nice private mail reply from Volker B., developper cited in[/FONT] [FONT=arial]the header of [/FONT][FONT=courier new]/etc/cups/cups-pdf.conf. [FONT=arial]

The options to choose the destination folder and/or the name of the newly created pdf file were operational at one point. However apparently Ubuntu devs have made changes that invalidated part of the configurability of cups-pdf.
There is no definite timetable for a new implementation, even though it is in the pipeline.

Interestingly, from the terminal, one can specify the pdf file name without a problem:
```
> lp -t test-filename -d *your-pdf-printer-name* ~/.bashrc 
request id is *your-pdf-printer-name*-79 (1 file(s))
> ls -AF ~/PDF
test-filename
```Volker pointed at the possibility to "**automatically post-process**" the result pdf file placed in *${HOME}/PDF*, by use of an ad-hoc script, declared with the *PostProcessing* key listed almost at the end of the conf file.

 I have not experimented with that as of yet, but I will at some point. 

There are two possibilities:

[LIST]
[*] - Terminal post-processing 
[/LIST]
[INDENT]i) Rename file
ii) Move renamed file to arbitrary directory, respecting permissions
[/INDENT]

[LIST]
[*]- GUI post-processing 
[/LIST]
[INDENT]Open a window where the user can rename the file in *${HOME}/PDF* and browse the tree to select a new destination directory.
[/INDENT]

The only two variables passed on to the post-processing scripts are *${USER}* and the pdf [FONT=courier new][FONT=arial]filename, for which I have no defined *${XYZ}* parameter.
[/FONT][/FONT][/FONT] [/FONT]

The reason you are running into this is because AppArmor (AA) is configured to protect you from malware's potential problems.  You could put AA into complain mode for the operation and live with the log files it generates or learn how to reprogram AA to direct the files to where you want them or just sym-link the directory to the location you prefer.  I did the last one myself.

---

### Post by Cbhihe on 2014-10-21
**@bab1**: Than you, I had no idea that AA was be the culprit. However I have never touched it and am not ready to invest the time.
Your idea to symlink [FONT=courier new]${HOME}/PDF[/FONT] only displaces the problem: viz. not choosing name and/or file saving location on a case by case basis.

Instead I'm trying  another route (if I could get it to work): _*automatic post-processing*_ of the newly created pdf file.  [FONT=courier new]cups-pdf[/FONT] provides that possibility, as seen in [FONT=courier new]/etc/cups/cups-pdf.conf[/FONT]. According to comments in the configuration files, the [FONT=courier new]PostProcessing[/FONT] key if left empty gives no post-processing. I set it to:
```
[FONT=Courier New]### Key: PostProcessing
##  postprocessing script that will be called after the creation of the PDF
### Default: <empty>[/FONT][FONT=Courier New]
PostProcessing /opt/bin/pp_cups-pdf[/FONT]
```
I scribbled [FONT=courier new][FONT=Courier New]/opt/bin/[/FONT]pp_cups-pdf[/FONT] in a jiffy last night and gave it permissions [FONT=Courier New]750 or -rwx**[COLOR=#cc0000]r-x[/COLOR]**---[/FONT] so [FONT=courier new]${USER}[/FONT] may actually execute it as a member of its group, with group permission [COLOR=#cc0000]**[FONT=Courier           New]r-x[/FONT]**[/COLOR]. Simple (i.e. not subtle) and works well when called from the terminal.  ```
[FONT=Courier New]
#!/bin/bash
#######
# /opt/bin/pp_cups-pdf
# Post-processing script to 
# - open last pdf file created by cups-pdf virtual-printer
# - rename and save it
# - remove it
[FONT=Courier New][FONT=Courier New]#######

DISPLAY[/FONT][/FONT]=*_my-hostname_*:0[FONT=Courier New]; export DISPLAY[/FONT]
FILE="$(\ls -Ac $HOME/PDF | head -1)"  # picks file with most recent ctime
/usr/bin/evince ${HOME}/PDF/$FILE &

notify-send "CUPS-PDF: $FILE was correctly post-processed"[/FONT]
[FONT=Courier New][FONT=Courier New]sleep 60 ; \rm -f [/FONT][/FONT][FONT=Courier New][FONT=Courier New][FONT=Courier New]${HOME}/PDF/$FILE &
[/FONT][/FONT]exit 0[/FONT]
```When called from the [FONT=courier new]cups-pdf[/FONT] via its configuration file, nothing happens. 
Any suggestion as to what may be wrong is warmly welcome.
-ced

---

