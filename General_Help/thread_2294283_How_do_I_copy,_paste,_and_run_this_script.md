---
title: "How do I copy, paste, and run this script?"
date: 2015-09-10
forum: General Help
---

### Post by Boyntonstu on 2015-09-10
This a part of an install script for a Brother printer.

The file is in Downloads.

I  can open the file, select all, and copy the text.

I need the steps on how to place the text in Terminal and run it.

This is part of the file:  linux-brprinter-installer-2.0.0-1



ENABLE_FAX_INSTALL=No           # change to Yes if FAX is required 

DEBUG_MSG=0
MSG=1


COLOR='\033[1;31m'
COLOR2='\033[1;35m'
COLOR3='\033[1;32m'
COLOR4='\033[1;34m'
MONO='\033[1;0m'

if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
  MESSAGE010="USAGE:  "
  MESSAGE012="     :  "
  MESSAGE020="  model"
  MESSAGE030="   -f model"
  MESSAGE040="   -l "
  MESSAGE050="Only root can perform this operation."
  MESSAGE060="CUPS is not installed."
  MESSAGE070="Do you want to specify a PROXY server? [y/N] ->"
  MESSAGE080="Enter the URL of the PROXY server."
  MESSAGE090="   ex http://(proxy-server-url):sad:port)"
  MESSAGE100="   ex http://(login-name):sad:password)@(proxy-server-url):sad:port)"
  MESSAGE110="     ->"
  MESSAGE120="Unable to get the server information."\
"  Please check the network settings."
  MESSAGE121="Input model name ->"
  MESSAGE122="Rpm or dpkg is required."
  MESSAGE130="Driver-packages cannot be found."
  MESSAGE140=" Confirm the model name."
  MESSAGE150="You are going to install  following packages."
  MESSAGE160="OK? [y/N]  ->"
  MESSAGE165="OK? [Y/n]  ->"
  MESSAGE170="Do you agree? [Y/n] ->"
  MESSAGE180="Do you agree? [Y/n] ->"

---

### Post by monkeybrain20122 on 2015-09-10
[https://answers.launchpad.net/ubuntu/+question/249202](https://answers.launchpad.net/ubuntu/+question/249202)

---

### Post by Boyntonstu on 2015-09-10
Thanks,

Problem solved!

---

