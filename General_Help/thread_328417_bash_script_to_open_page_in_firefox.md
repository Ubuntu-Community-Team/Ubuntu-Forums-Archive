---
title: "bash script to open page in firefox"
date: 2006-12-30
forum: General Help
---

### Post by munkar on 2006-12-30
so i found a cool script that allows me to open a web page in firefox from bash, but somehow when it runs, bash doesn't return to the prompt; i have to hit ctrl-c for the prompt to reappear.

the script is below. i don't fully understand it, but it looks like the ampersand that would need to be there to make it run in the background is there, but something is still going wrong:

```
#!/bin/bash
# 
# This scripts opens the urls in existing instance of firefox
# it uses a new-tab without showing annoing alert about used profile 
# 
# Name: mozilla-firefox
# Requirements: firefox, bash, pwd, grep ;-)
#
# Daniel Kmiec 
# 19.05.2004
#

#if no parameter is given det the default url 
if [ -z $@ ]; then
default_url="http://www.google.com"
else
   default_url=$@
fi
# check if we want to open url or a file
# if the specified file exists we use openfile
if [ -f $default_url ]; then 
   pwd=`pwd`
   dir=`dirname $default_url`
   is_not_relativ=`echo $dir | grep -E "^/"`
   
   if [ -z $is_not_relativ ]; then #is relativ
      default_url=$pwd/$default_url
      echo $default_url
   fi
((firefox -remote "openfile ($default_url, new-tab)" || firefox $default_url) >/dev/null) &
else
   ((firefox -remote "openurl ($default_url, new-tab)" || firefox $default_url) >/dev/null) &
fi

```

ideas?

---

