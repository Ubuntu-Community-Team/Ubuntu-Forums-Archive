---
title: "OO2.2 Spreasdsheet now crashes on Feisty"
date: 2007-04-24
forum: General Help
---

### Post by fjm03 on 2007-04-24
Beginning this am, Open Office 2.2 Spreadsheet crashes.

It will not open an existing document nor will it allow any data entry into a new document

Until this am, the program had been working properly on a clean install of 7.04. The syslogs provide no clue as to the problem.

I have completely removed OO 2.2 and reinstalled it via SPM to no avail. My next step will be to clean install 7.04 and start over.

Any insight would be appreciated before I undertake an unnecessary chore,

---

### Post by fjm03 on 2007-04-24
Problem resolved  .... with a little research.

A known bug in OO2.2 Spreadsheet.

Open Office 2.2 Spreadsheet (Calc) crashes when a CUPS printer is configured on the same system.

---

### Post by dcstar on 2007-04-24
> **fjm03 said:**
> Problem resolved  .... with a little research.

A known bug in OO2.2 Spreadsheet.

Open Office 2.2 Spreadsheet (Calc) crashes when a CUPS printer is configured on the same system.

What!, I had this reported as Launchpad OO bug a couple of weeks ago and it was a mystery back then, I haven't heard anything since....

Can you let me know where the listing you found is?

Edit: I have just confirmed that the CUPS issue causes my problem.

---

### Post by fjm03 on 2007-04-24
**This post could be related to an Ubuntu bug filed at**: Brother provided. [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/83950](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/83950)

That bug is still with me and I suspect it won't go away until I've modified the CUPS wrapper install which Brother provided.

Deleting the network printer stops the OO crashes with docs that are stored on the my home directory but not with docs stored on a local, network server. When opening docs stored outside the home directory, the OO splash screen presents, the progress bar dashes across the splash screen and then poof, OO is gone, whether Metacity or Beryl. Reminiscent of a classic, focus stealing problem.

I will admit frustration with Feisty, especially since my upgrade from Edgy was forced by a suspicious, critical lapse in the Edgy repo just after Conical  released Feisty.  After installing Feisty, I first encountered the hidden switch problem;  Beryl wouldn't play, regardless of install method, until an obscure switch in the System>>Preferences menu is thrown. Then I discovered that Feisty didn't like a VMware Server without long hacking sessions. Now I've stumbled on real bugs with OO2.2.   I've been reduced to a VMware  player in order to view my financials with MS Office.

Ain't Feisty grand!

---

### Post by dcstar on 2007-04-25
> **fjm03 said:**
> **This post could be related to an Ubuntu bug filed at**: Brother provided. [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/83950](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/83950)

That bug is still with me and I suspect it won't go away until I've modified the CUPS wrapper install which Brother provided.
..........
Ain't Feisty grand!

Yep!

I followed some other instructions and re-installed my Brother HL-2040 printer in CUPS (using the Brother web site Linux drivers), and now my OO 2.2 doesn't crash on opening a spreadsheet - woo hoo!

I'm so happy I'm back to where I was 4 weeks ago........                :confused:

---

