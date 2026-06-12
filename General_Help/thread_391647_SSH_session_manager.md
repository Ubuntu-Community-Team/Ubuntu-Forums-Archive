---
title: "SSH session manager"
date: 2007-03-23
forum: General Help
---

### Post by jakev383 on 2007-03-23
I run several servers from my laptop. In Windows I used to use PuTTY which was great. I have it installed for Ubuntu as well, but it leaves some to be desired (copy and paste is impossible AFAIK).
I decided to go looking for some other programs before I resort to writing a menu system in dialog or something to keep track of all my SSH sessions.
I found SSHMenu ([http://www.mclean.net.nz/ruby/sshmenu/#config](http://www.mclean.net.nz/ruby/sshmenu/#config)) which was nice. Only problem I had was that I could not specify the port and when I tried (hostname:port) it would die horribly. Too bad too. No obvious link to the author's emails to see about fixing it, and I don't program in Ruby.
I also found GRCM ([http://grcm.sourceforge.net/index.html](http://grcm.sourceforge.net/index.html)) which while not specifically for SSH sessions looked like it might have worked. Wrong. Had to install the deps for libgnomeui-2.0 and I could never get it to connect to a server. Maybe also had something to do with the fact that I'm not running SSH on port 22, but I tried several ways to define a port in the config screen for a connection to no avail.
Has anyone else found anything that works well? The servers I connect to are on various ports, so changing the ssh_config is not economical.
Thanks in advance!

---

### Post by djf_jeff on 2007-03-23
You can try [http://www.oronetes.net/webs/gnome-sshman/](http://www.oronetes.net/webs/gnome-sshman/)

You can specify the ssh port and other options.

---

### Post by jakev383 on 2007-03-23
> **djf_jeff said:**
> You can try [http://www.oronetes.net/webs/gnome-sshman/](http://www.oronetes.net/webs/gnome-sshman/)

You can specify the ssh port and other options.

Thanks. I'm trying it out right now. The Nautilus portion isn't working for me, but that's not something I used before anyway.
Thanks!

---

### Post by jakev383 on 2007-03-23
> **jakev383 said:**
> Thanks. I'm trying it out right now. The Nautilus portion isn't working for me, but that's not something I used before anyway.
Thanks!
DOH! I guess it's a Python script, so having multiple hosts on the same IP craps out. Maybe I can work around... Already tried aliases in my ssh_config file and turning strict checking off and neither seemed to work....

---

### Post by jakev383 on 2007-04-05
For those that are interested.... I needed to be able to copy and paste somewhat easily in my SSH sessions, so I hacked together a quick script using Dialog that gives me a menu of my SSH sessions. Since it uses gnome-terminal for initiate the SSH tunnels, copying is just Ctrl-Shift-C and pasting is just Ctrl-Shift-V.
Here's a snippet of the script I put together:
```

#!/bin/sh
a1_initialization() {

# set a temp file for the working scratch. $$ is the current shell ID.
tempfile=`tempfile 2>/dev/null` || tempfile=/tmp/$me.$$

# make sure the tempfile is deleted when we're done
trap "rm -f $tempfile" 0 1 2 5 15

# define the window title, caption and size attributes
TITLE="SSH Menu"
CAPTION="\
You can use the UP/DOWN arrow keys and enter to select item."
W_HEIGHT=20
W_WIDTH=75
W_MENU_HEIGHT=15
}

#####################################################################
## display the menu and process the selection
#
a5_process_menu(){

${DIALOG:=Xdialog} --clear \
      --title "$TITLE" \
      --menu "$CAPTION" $W_HEIGHT $W_WIDTH $W_MENU_HEIGHT \
            "Home" "Home Server" \
            "Firewall1" "Client 1 Firewall" \
            "FileServer1" "Client 1 File Server" \
             "qtp" "QTP Server" 2> $tempfile


case $? in
  0 )
    b55_process_selection
    ;;
  1 )
#   No or Cancel button was pressed
    break
    ;;
  2 )
#   Help button was pressed, if present
    break
    ;;
  3 )
#   Extra button was pressed, if present
    break
    ;;
  -1 )
#   errors occured, or exited via the ESC key
    break
    ;;
  * )
#   undefined return code
    break
    ;;
esac
}

#####################################################################
## process the menu selection
#
b55_process_selection(){

case `cat $tempfile` in
case `cat $tempfile` in
  "Home" )
    command="gnome-terminal -e /home/jake/.bin/homeserver"
    ;;
  "Firewall1" )
    command="gnome-terminal -e /home/jake/.bin/firewall1"
    ;;
  "Fileserver1" )
    command="gnome-terminal -e /home/jake/.bin/server1"
    ;;
  "qtp" )
     command="gnome-terminal -e /home/jake/.bin/qtp"
    ;;
* )
#   shouldn't get here, but break just in case (breaks the loop, actually :) )
    break
    ;;
esac

echo "Issuing command: $command"
$command

echo
echo -n " --- Hit ENTER to return to menu --- "
read
}

#####################################################################
## begin main processing here
#


a1_initialization

while true; do
  a5_process_menu
  break
done

exit 0


```

I created a folder in my home called .bin and put little scripts to actually log into my machines in there. Allows me to log into different ports and all.
Hopefully that helps someone out there. You'll need the dialog package to see the pretty menu.

---

### Post by gmclean on 2007-04-24
> **jakev383 said:**
> I found SSHMenu ([http://www.mclean.net.nz/ruby/sshmenu/#config](http://www.mclean.net.nz/ruby/sshmenu/#config)) which was nice. Only problem I had was that I could not specify the port and when I tried (hostname: port) it would die horribly.

There's nothing magic about the syntax for specifying a port number - SSHMenu simply passes all the options you specify to /usr/bin/ssh.  So to connect to host neptune on port 6422 enter this:

[FONT="Courier New"]-p 6422 neptune[/FONT]

See [FONT="Courier New"]man ssh[/FONT] for other options.

---

