---
title: "Displaying motd.dynamic in x-terminal-emulator tab"
date: 2018-07-06
forum: General Help
---

### Post by peter-drealm on 2018-07-06
I searched a lot for the answer to this one before brewing my own.  It may be obvious but I've not seen a good answer.

Given that you want your first X Terminal tab in a window opened from your window manager to get /run/motd.dynamic displayed, you actually need that file to exist.

So, three problems:
1) Make the first tab be a login shell.  I use KDE and Konsole here.[INDENT]Pop up the "Edit Application" on the Konsole icon in the start menu.  In the application tab, set the command to "konsole -e bash --login".  This change gets bash to run your .profile.
[/INDENT]
 
2) Get the .profile to display the /run/motd.dynamic file.  This is, of course, pretty simple:
```
# if running under X
if [ -n "$DISPLAY" ]; then
    # Display MOTD
    cat /run/motd.dynamic
fi
```

3) Oh dear.  That didn't work -- file not found! -- /run/motd.dynamic gets created by pam.motd and we didn't actually log in yet.   So, change the above...
```
# if running under X
if [ -n "$DISPLAY" ]; then
    # Dirty hack to ensure MOTD exists
    test -f /run/motd.dynamic || ssh -i "$HOME/.ssh/id_rsa" localhost /bin/false
    # Display MOTD
    cat /run/motd.dynamic
fi
```
Now, you'll need to have set your ssh keys up right (add the id_rsa.pub to authorised_keys) but otherwise, pretty straightforward and only run when needed.

---

