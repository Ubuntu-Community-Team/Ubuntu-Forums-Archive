---
title: "Bluefish will not start"
date: 2008-01-21
forum: General Help
---

### Post by kordite on 2008-01-21
Running latest version of Ubuntu on a Dell Inspiron E1505 laptop. Bluefish will no longer start. I receive the "Starting Bluefish Editor" at the bottom and the pointer clocks for 15 seconds and then it goes away. I have uninstalled and completely uninstalled in Synaptic. I have done a remove and purge from the terminal and reinstalled all to the same result. 

Earlier this month I had Firefox damaged by an installation of the FireFTP extension gone awry. It too would clock and not open. I had to completely remove, purge and reinstall Firefox to restore its functioning and even after that, I could not get the NoScript extension to install without crashing Firefox again.

I had used Bluefish without issue on the 13th of January, after the crash and restore of Firefox (on the 3rd of January) so I don't believe the two are actually related though the symptoms are similar.

Any suggestion on my next course of action?

---

### Post by finer recliner on 2008-01-21
did you remove your personal settings directory for bluefish (~/.bluefish)?

if you haven't, try removing (or renaming) said directory and then reinstalling bluefish using synaptic.

---

### Post by nemilar on 2008-01-22
I agree with the above poster, try removing your ~/.bluefish directory and see if that helps.

You might be able to get more information on the exact cause of the problem if you try starting bluefish from the command line, instead of through the GUI.

---

### Post by kordite on 2008-01-22
> did you remove your personal settings directory for bluefish (~/.bluefish)?

Yes I did and that didn't work. 

> You might be able to get more information on the exact cause of the problem if you try starting bluefish from the command line.

I hadn't tried that. "bluefish" at the command line starts right away. I noticed that the bluefish icon remained in the "Other" menu after I uninstalled. The command line for that was.

bluefish -n -p %f

I uninstalled. Deleted that lurking menu item. Reinstalled. A new menu icon didn't appear. I found bluefish in the menu "Programming" but it wasn't selected. It had the command line:

bluefish %f

I checked that box to have that appear in the active menu and it worked!

So, the issue would appear to have been in the qualifiers of the command. I'll have to look into that further as to what those qualifiers do and how they would get changed but it is working now. Thanks for the investigatory clues to lead me down the right troubleshooting path.

---

