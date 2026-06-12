---
title: "[SOLVED] Ubuntu 7.10 Can't print to Win XP Shared Printer"
date: 2007-12-14
forum: General Help
---

### Post by techiebiker on 2007-12-14
Hope someone can help. I've read through posts about similar problem and been unable to resolve from those suggestions.

Have Ubuntu 7.10 and am attempting to print to shared printer on WinXP Pro.

What works...
From Ubuntu ping XP Pro works. Avg round trip less than 2 ms
From Ubuntu accessing file shares on XP Pro box that also has printer share works
From a 2nd XP Pro box can print to shared printer that I can't get at with Ubuntu

What doesn't work, printing from Ubuntu to XP Pro shared printer...

In Ubuntu, from System>Administration>Printing menu item
1. "Server Settings" selected in list on left of dialog
2. click "New Printer" icon
3. select "Windows Printer via Samba" from list
4. click "Browse..." button to right of "smb://" text field
5. SMB Browser window appears
5.1. Workgroup name "Home" is displayed (this is correct Windows workgroup name on XP computer), click triangle to expand
5.2 After expansion computer name "Dell" is displayed, Click triangle to expand (This has the shared printer attached.)
5.3 No names appear in list after expanding.

SO... go back to step 3 and start again from there...
4a. in "smb://" field enter 'home/dell/samsung'
5a. click "Authentication required" check box.
6a. type 'Guest' in "Username:" field
7a. leave "Password:" field blank (guest acct has no password on XP Pro box)
8a. click "Verify" button, message is displayed almost immediately "Inaccessible - This print share is not accessible"

SO... go back to step 3 and start again from there...
repeat step 4a through 8a except change text in "smb://" field to 'dell/samsung'
Same result

SO... go back to step 3 and start again from there...
repeat step 4a through 8a except change text in "smb://" field to '192.168.0.5/samsung'
Same result

This same XP Pro print server and printer used to be available when the Ubuntu box was 6.06. Did a clean install, yes repartition and format, for 7.10 and haven't been able to print from Ubuntu since. Have turned off firewall and antivirus on XP box in case those are culprits. Makes no difference and the other XP box can print to the shared printer when those services are running.

I'm also able to use VNC on the Ubuntu box to remote the XP Pro box. 

The only thing remotely interesting in the XP Pro log is in the Security log. It showed successful account logon attempts from the Ubuntu computer, followed by unsuccessful logon/logoff and made reference to an application on the XP box called Acronis. So I uninstalled Acronis. Now the log shows successful account logon attempts from the Ubuntu computer, followed by unsuccessful logon/logoff from the NT AUTHORITY SYSTEM. The times of these log entries coincide with the times I attempt to set up the printer.

I'm thinking it must be something on the Ubuntu side BECAUSE IT WORKED IN 6.06. The stuff showing up in the XP log is likely the clue about what's changed and what I need to modify in Ubuntu but I'm not getting the clue.

Anybody have any suggestions?

---

### Post by techiebiker on 2007-12-16
I found one solution. Don't like it because I'm pretty certain with 6.10 anonymous connections were allowed. Of course there have been a number of Windows updates since then so maybe they changed something.

In any case, the following works:
6a. type '<interactive user account name other than Guest>' in "Username:" field
7a. in "Password:" field type password for user name from 6a

All interactive users on WinXP box, except administrator, are members of "Users" group not "Power Users" so don't feel too at risk. Still a bit concerned about having to provide an interactive user account and password on the Ubuntu box to get printing working.

---

