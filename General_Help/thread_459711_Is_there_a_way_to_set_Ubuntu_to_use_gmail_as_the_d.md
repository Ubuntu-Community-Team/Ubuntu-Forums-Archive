---
title: "Is there a way to set Ubuntu to use gmail as the default mail app?"
date: 2007-05-30
forum: General Help
---

### Post by rainwalker on 2007-05-30
Right now Thunderbird is set as the default app to handle email, but I don't actually use it. I use gmail instead, only keeping Thunderbird cause some messages are stored in it, and I was wondering if there's something I can install that will allow me to set gmail as the default.

Any suggestions?

---

### Post by konungursvia on 2007-05-31
Don't think so my friend, as Gmail is not an app itself, per se, but a (beta!) website. I think you can set the default mailto as your gmail, when using Opera or Firefox, but I think that's probably it.

---

### Post by rainwalker on 2007-05-31
Ah. Well I ask only because my friend said there's some windows thing you can do that lets you set the default as gmail so I didn't know if there was something similar for Linux. 

Thanks anyway  :)

---

### Post by ep2011 on 2007-05-31
There is. I use it.

First, make a file in your home folder called open_mailto.sh. Open it in gedit (or your favorite text editor) and add to the file:

> #!/bin/bash
##
## gmail_link 1.2
##
## gmail_link makes it possible for mailto links to work with Gmail and
## other web-based e-mail. This file is the main script. If you only
## use one browser, you may call it directly. Otherwise, use
## gmail_link_select_browser.
##
## Copyright (c) 2007 Scott Severance <http://www.scottseverance.us>
## 
## This program is free software; you can redistribute it and/or modify
## it under the terms of the GNU General Public License as published by
## the Free Software Foundation; either version 2 of the License, or
## (at your option) any later version.
## 
## This program is distributed in the hope that it will be useful,
## but WITHOUT ANY WARRANTY; without even the implied warranty of
## MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
## GNU General Public License for more details.
## 
## You should have received a copy of the GNU General Public License
## along with this program; if not, write to the Free Software
## Foundation, Inc., 59 Temple Place - Suite 330,
## Boston, MA 02111-1307, USA.


####################################################################
## Configuration section
####################################################################

# Set the default browser here; mainly useful if you're NOT using
# gmail_link_select_browser.
browser='firefox'

# Set the webmail format string; it uses printf(1) formatting.
# This should be the URL of your webmail's compuse function. The
# order of parameters is: to, subject, body, cc, bcc.
#
# To use a webmail provider other than the default (Gmail), remove
# the # sign from the appropriate formatString line and put a # in
# front of Gmail's formatString line.
#
# Thanks to Jed Brown, the author of the Firefox WebmailCompose
# extension, for many of these format strings. Steve Severance
# provided the Gmail string, and I fixed Jed Brown's Yahoo! string.
# The others haven't been tested yet, as I don't have an account
# with the other providers and I'm not interested in creating an
# account.

# Gmail string
formatString="http://mail.google.com/mail/?view=cm&fs=1&tf=1&to=%s&su=%s&body=%s&cc=%s&bcc=%s"

# Yahoo! Mail string
#formatString="http://compose.mail.yahoo.com/?To=%s&Subj=%s&Body=%s&Cc=%s&Bcc=%s"

# Hotmail string
#formatString="http://hotmail.msn.com/cgi-bin/compose?To=%s&Subject=%s&Body=%s&Cc=%s&Bcc=%s&mailto=1"

# Mail.com string
#formatString="http://mail01.mail.com/scripts/mail/Outblaze.mail?composeto=%s&subject=%s&body=%s&cc=%s&bcc=%s&compose=1"

# Netscape Mail string
#formatString="http://webmail.netscape.com/compose.adp?mailto=%s&mailsubject=%s&mailbody=%s&mailcc=%s&mailbcc=%s"

# Opera Mail string
#formatString="http://mymail.operamail.com/scripts/mail/Outblaze.mail?compose=1&did=1&a=1&to=%s&subject=%s&body=%s&cc=%s&bcc=%s"

# Horde string -- BE SURE TO FILL IN YOUR HORDE DOMAIN NAME (AND
# PATH, IF APPLICABLE)!
#formatString="http://YOUR_HORDE_DOMAIN_NAME_HERE.com/horde/imp/compose.php?popup=0&to=%s&subject=%s&msg=%s&cc=%s&bcc=%s"

# Squirrel Mail string -- BE SURE TO FILL IN YOUR SQUIRREL MAIL
# DOMAIN NAME (AND PATH, IF APPLICABLE)!
#formatStr="http://YOUR_SQUIRREL_MAIL_DOMAIN_NAME_HERE.com/src/compose.php?send_to=%s&subject=%s&body=%s&send_to_cc=%s&send_to_bcc=%s"


####################################################################
## End configuration
####################################################################


returnVar=
E_USAGE=2
E_ERROR=1

function usage {
    echo "Usage: $(basename $0) link-text [browser]"
    exit $E_USAGE
}

function callBrowser {
    local ua="$1"
    local url="$2"

    if [[ $ua == 'opera' ]]; then
        opera --remote "openURL($url,new-page)"
    else $ua "$url"
    fi
}

function parseURL {
    local url="$1"
    local target="$2"
    local ua="$3"
    local separator="$4"
    local sedStr=

    [[ -n $separator ]] || separator='&'

    case "$target" in
        "to")
            if [[ $ua == 'opera' ]]; then sedStr='^\(.*\)$'
            else sedStr="^mailto:\([^${separator}?]*\).*"
            fi
            ;;
        "subject") sedStr=".*subject=\([^${separator}]*\).*" ;;
        "body") sedStr=".*body=\([^${separator}]*\).*" ;;
        "cc") sedStr=".*[^b]cc=\([^${separator}]*\).*" ;;
        "bcc") sedStr=".*bcc=\([^${separator}]*\).*" ;;
        *) echo "The target $target hasn't been implemented yet." > /dev/stderr; exit $E_ERROR ;;
    esac
    
    returnVar="$(echo "$url" | sed "s/${sedStr}/\\1/g")"
    [[ $returnVar == $url && ($ua != 'opera' || ($ua == 'opera' && $target != 'to')) ]] && returnVar=
}

function buildGmailURL {
    local url="$1"
    local ua="$2"
    
    parseURL "$url" "to" "$ua"
    local to="$returnVar"

    parseURL "$url" "subject" "$ua"
    local subj="$returnVar"

    parseURL "$url" "body" "$ua"
    local body="$returnVar"
    
    parseURL "$url" "cc" "$ua"
    local cc="$returnVar"
    
    parseURL "$url" "bcc" "$ua"
    local bcc="$returnVar"

    returnVar="$(printf "$formatString" "$to" "$subj" "$body" "$cc" "$bcc")"
}

function main {
    [ "$#" -lt 1 -o "$1" == '--help' ] && usage

    local link="$1"
    if [ -n "$2" ]; then local ua="$2"
    else local ua="$browser"; fi
    
    buildGmailURL "$link" "$ua"
    local gmailLink="$returnVar"

    callBrowser "$ua" "$gmailLink"
    exit 0
}

main "$@"

Now, go to System -> Preferences -> Preferred Applications.

On Mail reader, change it to custom and in the box under it type:

> 
/home/*username*/open_mailto.sh %s

If you have any problems just post.

Edit: This is assuming you use firefox, if you don't, then change browser='firefox' near the top to browser='opera' (example, if you don't use opera, change it to something else)

---

### Post by rainwalker on 2007-05-31
Thanks! I'll post next time I try it

---

### Post by ep2011 on 2007-05-31
> **rainwalker said:**
> Thanks! I'll post next time I try it

No Problem. Good luck :)

---

### Post by cstudent on 2007-05-31
I actually do it by following this howto:

[http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html](http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html)

---

### Post by ep2011 on 2007-05-31
> **cstudent said:**
> I actually do it by following this howto:

[http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html](http://matthew.ruschmann.net/blog/Linux/gnome-gmail-1.1.html)

Does it work if the mail:to links have subjects, bcc, cc, etc? I found tons of others that didn't, this is the only one so far that did.

---

