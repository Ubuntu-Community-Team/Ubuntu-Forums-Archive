---
title: "Nautilus Delete Confirmation"
date: 2007-10-30
forum: General Help
---

### Post by kwkard on 2007-10-30
I've just installed Gutsy and am really enjoying it. I have a minor problem with deleting files in nautilus. When I highlight an item and press the delete key, it permanently deletes it with no confirmation! This is on a NTFS partition. Doing the same thing on an ext3 partition moves the file to the trash without confirmation.

I've gone to Edit -> Preferences -> Behavior and checked 'Ask before emptying the trash or deleting files.  But that only seems to happen when clicking on empty trash.

Also, there is no .Trash folder in the root of the NTFS folder. There is also no confirmation or warning when dragging from an NTFS volume to the trash can. I ran:

gconftool-2 -g /apps/nautilus/preference/confirm_trash
>>>No value set for `/apps/nautilus/preference/confirm_trash'

So then I ran:

gconftool-2 -s /apps/nautilus/preference/confirm_trash --type=bool true
gconftool-2 -g /apps/nautilus/preference/confirm_trash
>>>true

Any idea what's going on here? Is there no way to enable a confirmation dialog when deleting from an NTFS volume?
And if not, is there a way to disable the keyboard binding for the delete key in nautilus?
Thanks.

---

### Post by rsambuca on 2007-10-30
On an ntfs partition, the deleted files just go to a hidden folder called '.Trash-<yourusername>'.  If you are in nautilus, you can see this folder by selecting "View Hidden Files" from the top menu.  You can then just delete this folder.  It will re-appear when you delete something on the ntfs drive.  You might want to note that the free space available on an ntfs drive will not go up if you do not delete this hidden folder.

---

### Post by kwkard on 2007-10-31
Thanks for your response, I had enable Show Hidden Items before and the .Trash folder didn't show up, I also issued ls -a at the terminal and it wasn't there either. But for some odd reason it's there now?:confused: Somehow changing settings back and forth several times must have done the trick. Thanks again.

---

