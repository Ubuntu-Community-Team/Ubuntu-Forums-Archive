---
title: "Running script when computer goes active/inactive?"
date: 2012-10-28
forum: General Help
---

### Post by azzid on 2012-10-28
I've been issued a decree by my significant other to make sure I turn my computer monitors off before bed at night (the soft poweroff the operating system does is not enough). I cannot seem to remember to do this, so I'm looking for a way to have my computer manage this by itself.

I have the ability to manage the power outlets to the monitors from the command line since I have a [TellStick Duo]("http://www.telldus.se/"), but I have been unable to get the proper command to run at the proper time.

I found a perl script from the gnome-screensaver developers which I modified to have the monitors power killed or restarted depending on the screensaver activity:
```
#!/usr/bin/perl
use strict;
use warnings;
use 5.010;

my $cmd = "dbus-monitor --session \"type='signal',interface='org.gnome.ScreenSaver',member='ActiveChanged'\"";

open (IN, "$cmd |");

while (<IN>) {
    chomp (my $date = `date`);
    if (m/^\s+boolean true/) {
        print "*** Screensaver is active\t\t$date ***\n";
        # Kill monitors
        `tdtool --off 4; tdtool --off 5`;
    } elsif (m/^\s+boolean false/) {
        print "*** Screensaver is no longer active\t$date ***\n";
        # Reanimate monitors
        `tdtool --on 4; tdtool --on 5`;
    }
}
```

I does however not turn the monitors on until I've successfully entered my password on the screensaver lock screen. Typing "in the blind" feels a bit iffy and will probably cause problems sooner than later.

The screensaver has two different states even when active, it either shows the screensaver, or the login dialog. I'd like to trigger my script to turn on the monitor when the login dialog is showing but I've been unable to figure out if there is a proper way to catch that state change.

Does anyone have a suggestion on how I can trigger on something like mouse activity rather than successful login when it comes to starting the monitors?

---

