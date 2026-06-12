---
title: "CUPS Backend setting up permission and create directory"
date: 2014-10-22
forum: General Help
---

### Post by kam3 on 2014-10-22
Hi I am using sh shell script which requires: 

Required command line parameters and parameter order
• Required output (format) from CUPS server backend query
• Required permissions and locations to install the backend

SO this is what I have done: 

#!/bin/sh
# PDF writer backend for cups


# some tools we need
CHMOD=/bin/chmod
CHOWN=/usr/sbin/chown
CHGRP=/usr/bin/chgrp
PS2PDF=/usr/local/bin/ps2pdf


# log call to /var/log/messages
logger "pdf-writer: $@"


# printer detection
if [ $# -eq 0 ] ; then
  echo "file pdf:/home/PDF \"Unkown\" \"PDF Printer\" " 
  exit 0
fi


JOB=$1
# put other command line parameters in variables


# create output directory if not exists
DIR="/home/PDF/${USER}"
if [ ! -d $DIR ] ; then
  # create directory and set permissions/owner/group
fi


DATE=`date +"%Y%m%d%H%M%S"`
PDFFILE="${DIR}/${TITLE}_${DATE}.pdf"
# convert postscript to pdf and set permissions/owner/group
# of pdf file


exit 0


I am not sure how to setup permission.

Do you just use chmod  to set permission ?

---

