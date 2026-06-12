---
title: "Muon refusing to install updates"
date: 2023-10-27
forum: General Help
---

### Post by David_Partridge on 2023-10-27
Muon used to prompt for authorisation but no longer does so and it always fails with an error 

Saying "This operation cannot continue since proper authorisation was not provided"

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal

David

---

### Post by MAFoElffen on 2023-10-27
Wow. That's an alternative package manager that I have not heard anyone ask about in years. It's code and version is still based on what was released in January 2011. It used to be used in KDE and Lubuntu... But I do see that package is still built through Noble (24.04)

Launchpad is still marked as the maintainers for the Ubuntu repo package. 

Here is your Bug: [https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346)

It was filed on 2020-04-27 (over 3 years ago), but is still marked as "New"... Same situation and description as yours. 

What I would do is join that bug as "Yes, it affects me"... Then post a comment to it, asking them if it has been worked on resolved, because you are having the same issue. Also note that you notice it was filed in over 3 years ago, and was not even triaged. Ask them if you should join that stagnant Bug Report or file a new Bug Report so that it collects and submits your system information. That it seems to be a known problem that is not resulted... (That would lay on some guilt and shame.)

Adding to that Bug Report may add weight to it, for them to see that it was not an isolated event. If they ask you to report a new Bug, then with it linked between the two reports , that will also add more weight to it to get resolved.

---

### Post by guiverc on 2023-10-28
David can I request you add more system details on [https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346/comments/2](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346/comments/2)

ie. I've seen this thread, thus know you're using Ubuntu 20.04 LTS, but what desktop are you using; as `muon` is still supported & maintained (for 22.04 & newer anyway; the flavors no longer support 20.04), but Kubuntu/KDE 20.04 and Lubuntu/LXQt 20.04 are already EOL & thus 20.04 is no longer supported by those flavors. I've seen a number of fixes for newer releases land since focal/20.04.

Also are  you using english?  with english/US keyboard?  as I'm aware of some issues where non-latin (non-english) type keyboards/language are used.  I'm pretty sure the *Original Poster *of that bug report is not using english/english.

The bug would need to be confirmed I suspect on a fully-supported release of the flavors before attention would be granted to it. Yes any MOTU can install a fix until 2025-April, but resources are limited.

---

### Post by SeijiSensei on 2023-10-28
Unless you need to pick packages to update via the GUI, I'd stick to the command line. Just these two commands are all you need:
```

sudo apt update
sudo apt upgrade

```
The first downloads the current package list for your distribution; the second installs any updated packages.

---

### Post by MAFoElffen on 2023-10-28
+1 with guiverc...

Like I said, if you include your system information, describe your problems as being the same, and touch on these points (re-quoted below), I think that will add weight to that bug and get it moving again.
> **MAFoElffen said:**
> 
...
Here is your Bug: [https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346](https://bugs.launchpad.net/ubuntu/+source/muon/+bug/1875346)
...
What I would do is join that bug as "Yes, it affects me"... [COLOR=#ff0000]Then post a comment to it, asking them if it has been worked on resolved, because you are having the same issue. Also note that you notice it was filed in over 3 years ago, and was not even triaged. Ask them if you should join that stagnant Bug Report **or file a new Bug Report so that it collects and submits your system information[SUP]*[/SUP]**. That it seems to be a known problem that is not resulted...[/COLOR] (That would lay on some guilt and shame.)

Adding to that Bug Report may add weight to it, for them to see that it was not an isolated event. If they ask you to report a new Bug, then with it linked between the two reports , that will also add more weight to it to get resolved.
All that is in your own personal interest to do, to help them be able to help you. I feel that will help move that along.

The policy for running apport-collect and submitting those reports to an existing bug at Launchpad is only done when the person handling the bug "there" approves that... That is why you would have to describe what you have, as guiverc suggested.

[SUP]*[/SUP] -- That's why I asked to you ask them if they need you to submit that "there" or in a new Bug report, if they needed more detailed information. In a New Bug Report, that is automatically done with ubuntu-bug...

Does that make sense to you?

---

