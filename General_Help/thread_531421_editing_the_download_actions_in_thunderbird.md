---
title: "editing the download actions in thunderbird"
date: 2007-08-21
forum: General Help
---

### Post by Specks on 2007-08-21
I'm using Thunderbird 1.5.0.12.

I'm trying to open a .xls file in open office from an email. When I double click on the file, I get the following error message:
> 
suchandsuchfile.xls could not be opened, because the associated helper application does not exist. Change the association in your preferences.


So I go to the menu: Edit -> Preferences. From there I select the Attachments tab then click the View & Edit Actions button.

There are no actions listed in the list. I search for xls, but nothing returns. The Remove Action and Change Action are grayed out. There is no button for adding an action.

What is going on. Do I need to upgrade to 2.0? Why isn't 2.0 listed in the synaptic package manager yet?

---

### Post by nanotube on 2007-08-22
this link will elucidate the situation:
[http://kb.mozillazine.org/Actions_for_attachment_file_types](http://kb.mozillazine.org/Actions_for_attachment_file_types)
(in brief, the actions panel in tb is under-implemented).

to upgrade to tbird2, see the ubuntuzilla project (link in my sig). though that won't change the situation with the download actions.

do you have either gnumeric or openoffice installed and associated with the .xls filetype? maybe that's why you are getting the error msg.

---

### Post by Specks on 2007-08-22
Removing the mimeTypes.rdf file in my profile seems to have fixed the problem. Now the .xls attachment is recognized and gives the option to open it with openOffice.

---

