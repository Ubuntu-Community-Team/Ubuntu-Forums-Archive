---
title: "Can curl be installed in Gusty?"
date: 2008-04-07
forum: General Help
---

### Post by bung on 2008-04-07
"curl" is not in in Gusty's arsenal. How can I install curl or modify the following script to make it to run? 

 "sudo apt-get install curl" reports the following

Package curl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package curl has no installation candidate

---------------------------------------------------------------------
THIS IS THE SCRIPT (by listener) that I want to run
---------------------------------------------------------------------
#!/bin/sh

# parameter 1: [email]username@bigpond.net.au[/email]
eMail="$1"

# parameter 2: Bigpond password
pWord="$2"

# parameter 3: time stamp used to log usage    # $(date "+%m%d%H%M") 
logTime="$3"

# parameter 4: name of file used to log usage
logFile="$4"

# page being retrieved using this method
result="https://my.bigpond.com/mybigpond/myaccount/myusage/default.d o"

# session strings
submit="https://telstra.com/siteminderagent/SMLogin/preLogin.do"
script="https://telstra.com/tcoma/security/login.asp"
target="$script?AUTH_REDIR=$result&BPCUSTLOGIN=Y"

# escaped strings
subst="sed -e s|%|%25|g -e s|&|%26|g"
subst="$subst -e s|/|%2f|g -e s|:|%3a|g"
subst="$subst -e s|;|%3b|g -e s|=|%3d|g"
subst="$subst -e s|?|%3f|g -e s|@|%40|g"
eMail=$(echo "$eMail" | $subst)
pWord=$(echo "$pWord" | $subst)
target=$(echo "$target" | $subst)

# command string
curl="curl -s -k -L --max-time 30 -b cookie -c cookie"

# clean startup
rm -f cookie frame?

# submit logon
data="user=$eMail"
data="$data&password=$pWord"
data="$data&final_target=$target"
$curl -o frame1 -d "$data" "$submit"

# request page
$curl -o frame2 "$result"

# refresh page
follow="$(sed -n 's|.*URL=\(.*\)\".*|\1|p' frame2)"
$curl -o frame3 "$follow"

# fetch result
$curl -o frame4 "$result"

# parse result
usage=$(sed -n -e 's|,||' -e 's|.*>\([0-9]\+\).*MB<.*|\1|* p' frame4)

# log results
echo $logTime $usage >> $logFile 

=-=-=========================

---

### Post by justleen on 2008-04-07
make sure you have all repositories enabled.. 

I cant try to download/install at the moment, but it does show up in
```

apt-cache search curl

```

---

### Post by bung on 2008-04-07
Presto! Problem solved. I enabled all repositories as suggested and 'curl' was there. Thank you justleen.

One other question regarding the script's parameters. 

# parameter 1: [email]username@bigpond.net.au[/email]
eMail="$1"

I know I can use:

eMail=username@bigpond.net.au

What other ways can I express this same thing?

---

