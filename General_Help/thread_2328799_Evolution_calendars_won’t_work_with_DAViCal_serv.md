---
title: "Evolution calendars won’t work with DAViCal serv"
date: 2016-06-24
forum: General Help
---

### Post by ubu12 on 2016-06-24
1. Upgraded to new 16.04 LTS version.
 
 
 2. Made a backup on Evolution data before changing over.
 File / Backup Evolution data   
 
 
 3. Fresh install of 16.04 LTS.
 
 
 4. Fresh install of Evolution 3.18.5.2 from Ubuntu repository using Synaptic.
 
 
 5. Reinstalled previous data.
 File / Restore Evolution data
 
 
 6. Opened Evolution and Mail and Contacts work fine, but Calendars will not load.
 Checking the box for a calendar titled Appointments so that it can be viewed results in this error message that appears in the upper right-hand corner of the window:
 Failed to open calendar 'CalDAV : Appointments'
 Unable to connect to 'Appointments': Error calling StartServiceByName for org.gnome.evolution.dataserver.Calendar7: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ChildSignaled: Process org.gnome.evolution.dataserver.Calendar7 received signal 11
 
 
 Same for all other calendars in that view.
 
 
 7. Data source for calendars is DAViCal server running on a Ubuntu 12.04 LTS server on the LAN.
 This has worked for years with no problems until this install of 16.04 LTS.
 
 
 8. Using VirtualBox, created a VM of the same 16.04 LTS Desktop. Installed Evolution to the VM and did not load any prior information or restore any backed up information. Created a new calendar connection to one of the calendars on the DAViCal server. It worked fine with no problems at all. This establishes that the DAViCal server is working fine, just as it always has.
 
 
 9. I believe that the Evolution installation or prior data that was backed up was corrupted somehow.
 
 
 10. Uninstalled Evolution hoping to create a fresh install from which I would manually create the connections to the calendars on the DAViCal server. The previous data appeared on the fresh installation with having been loaded onto it by me. This would indicate that the data is stored somewhere in my user profile and was not erased by the uninstallation of the Evolution program.
 
 
 11. Stuck with an untenable situation. I need some client for managing my calendars, contacts and email at all times and I don’t currently have one for my emails.
 
 
 12. Tried to manually reach calendars on DAViCal server by creating new calendar connection in Evolution which would refer to a calendar file path on the DAViCal server and when the Calendar authentication request window comes up, It has this line showing just above the box for inputing the password, “HTTP Error: Forbidden”.

---

### Post by QIII on 2016-06-25
Courtesy bump from the Staff.  :)

---

