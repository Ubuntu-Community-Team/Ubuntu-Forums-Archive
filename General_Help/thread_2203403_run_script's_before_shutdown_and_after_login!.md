---
title: "run script's before shutdown and after login!"
date: 2014-02-03
forum: General Help
---

### Post by senaps on 2014-02-03
hi....
i have a problem with my back light and that's that when i turn off my pc, and turn it on again, it doesn't remember my lcd backlight condition and goes back to the default...
so, i need to have a script who before turning off the compuetr, check's and saves the back light percentage and then, set's it after loging in to the system! :)...

so how can i do that?

---

### Post by mike134 on 2014-02-03
You can use solution at [http://askubuntu.com/questions/66751/how-do-i-set-default-display-brightness](http://askubuntu.com/questions/66751/how-do-i-set-default-display-brightness) to set your brightness to a specific level when you boot your PC which I find more useful than setting to the brightness level when you shutdown - i.e if you boot your PC at time X and shutdown at time Y, then when you next boot your PC, what you want your brightness to be depends on whether the ambient light is like it was at time X or time Y and for me it is more likely to be X, as if I don't want to use my PC for a short amount of time then I tend to hibernate or suspend, rather than shutdown.

If you want to set to the level to that when you shutdown, then you would need to change solution in URL above to as follows:

[FONT=courier new]# Install xbacklight in case it is not already installed (small).
sudo apt-get install xbacklight

# This creates a small script running xbacklight to set brightness to saved setting
sudo bash -c '{
echo "xbacklight -set \`cat /etc/lightdm/backlight.save\`"
echo "exit 0"
} > /etc/lightdm/display-setup-script.sh '

# This makes that script executable
sudo chmod a+rx /etc/lightdm/display-setup-script.sh

[/FONT][FONT=courier new]# This creates a small script to save xbacklight setting to a file[/FONT]
[FONT=courier new]sudo bash -c '{[/FONT]
[FONT=courier new]echo "val=\`xbacklight\`"[/FONT]
[FONT=courier new]echo "if [ \$? -eq 0 ]"[/FONT]
[FONT=courier new]echo then[/FONT]
[FONT=courier new]echo "  echo \$val > /etc/lightdm/backlight.save"[/FONT]
[FONT=courier new]echo fi[/FONT]
[FONT=courier new]echo exit 0[/FONT]
[FONT=courier new]} > /etc/lightdm/session-cleanup-script.sh '[/FONT]


[FONT=courier new]
# This makes that script executable
sudo chmod a+rx /etc/lightdm/session-cleanup-script.sh

egrep "display-setup-script|session-cleanup-script" /etc/lightdm/lightdm.conf

# If above command matches any lines then you will need to edit /etc/lightdm/lightdm.conf manually. else run the following command to run your above scripts on display startup and logout 
 
sudo bash -c '{
echo "display-setup-script=/etc/lightdm/display-setup-script.sh"
[COLOR=#222222]echo "session-cleanup-script[/COLOR][COLOR=#222222]=/etc/lightdm/[/COLOR][COLOR=#222222]session-cleanup-script[/COLOR][COLOR=#222222].sh"
} [/COLOR][COLOR=#222222] >>/etc/lightdm/lightdm.conf '

# Save current backlight level as changes in lightdm.conf are not effective until next login
[/COLOR]sudo bash -c 'xbacklight > /etc/lightdm/backlight.save'
[/FONT]
[FONT=courier new]# Make sure /etc/lightdm/backlight.save  can be written to by any user:
sudo chmod 666 /etc/lightdm/backlight.save[/FONT]


This solution uses session-cleanup-script to run xbacklight to save current backlight setting to /etc/lightdm/backlight.save (and if xbacklight fails then old value is left in file) when you logout  - see lightdm.conf in /usr/share/doc/lightdm/lightdm.conf.gz:
# session-cleanup-script = Script to run when quitting a user session (runs as root)

Changes in lightdm.conf do not take effect immediately, so the first time you log out, your backlight is not saved but all subsequent times you logout, your backlight setting should be saved.
I found that if xbacklight command fails in display-setup-script.sh then desktop won't start, which is why I added "exit 0" to display-setup-script.sh so that if xbacklight command fails, your desktop will still start.

If you have a problem where your desktop won't start, then press "ctrl-alt-F1" and login with normal username and then use:
[FONT=courier new]sudo nano /etc/lightdm/lightdm.conf 
[/FONT]
and remove the display-setup-script and session-cleanup-script lines and restart lightdm:
[FONT=courier new]service lightdm restart
[/FONT]
Mike

---

