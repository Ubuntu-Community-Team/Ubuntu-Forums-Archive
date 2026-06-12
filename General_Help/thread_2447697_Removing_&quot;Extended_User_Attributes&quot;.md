---
title: "Removing &quot;Extended User Attributes&quot;"
date: 2020-07-23
forum: General Help
---

### Post by andre46 on 2020-07-23
My Ubuntu MATE 20.04 VM has a weird issue with some files. Something has been adding a weird file attribute named: "DOSATTRIB" with no value. I can see this in the MATE file properties menu under "Extended user attributes". I haven't been able to track down what has been adding this yet. And I probably never would have noticed if this wasn't causing SMB issues. I'm not sure why, but any file that has this attribute appears in my Windows PC as a file folder with a grey "x" and the file is inaccessible from Windows. Once I remove the attribute, the file returns to properly being shared by SMB.

Is there a way to remove this attribute in bulk? Or what is this actually breaking? Is there a way for me to adjust permissions so that this attribute won't effectively break SMB for affected files?

---

### Post by Holger_Gehrke on 2020-07-23
The extended user attribute DOSATTRIB is used by samba to store the DOS file attributes (Archive, Read-Only, Hidden, System) for a file. So either somebody using a windows client played around with the file attributes for these files in the share or something else set them. There's a command line tool named setfattr, which allows you to manipulate extended user attributes. You could just run 'setfattr -x user.DOSATTRIB -- *' to clear the attribute. With getfattr - which allows you to see the attributes - and a bit of shell scripting you can probably create a list of the files which have a set DOSATTRIB.

Holger

---

### Post by andre46 on 2020-07-23
I'm the only one accessing the SMB share, and I do indeed access it with a windows 10 client. These are video files, so I can't imagine I changed anything other than the filename. But yeah, I just made bulk changes from my windows laptop, and it appears these all have that attribute set as well.

Outside of scripting, what would be my options? Is there a change to samba that I can make to prevent these files from effectively being inaccessible? I've been using this similar setup for years, and this is a new issue for me. My windows laptop hasn't changed, the only changes to my old NAS setup was essentially re-building it from a clean Linux install.

(Edit to clean up some wording above). Also, a bunch of the files I was having issues with yesterday were marked as Archived. I again have absolutely no idea why these were flagged as Archived. They were direct file copies from a different path, and the copying was initiated/performed on the Ubuntu machine, not via Windows. The original files I copied are not flagged as Archived in my Windows device. wtf.

---

### Post by andre46 on 2020-07-26
Ok, not technically solved, but I think we can close this. I've migrated all my NAS responsibilities to an OpenMediaVault server. When I was configuring the SMB shares, there was an option to ignore Extended User Attributes, which I simply left unchecked. This tells me this is probably something that would have been configurable via samba settings, however I'm not going to dig into this any more. Thank you for your assistance.

---

