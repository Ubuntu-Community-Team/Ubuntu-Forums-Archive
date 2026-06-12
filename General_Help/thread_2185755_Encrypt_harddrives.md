---
title: "Encrypt harddrives"
date: 2013-11-04
forum: General Help
---

### Post by mac666 on 2013-11-04
Hello!
I would like to encrypt my 4 harddrives, about 9tb of data. 
Its on a server running ubuntu desktop. 

A couple of questions: 

Is there any encryption that requires a key for each reboot? 
Would that result in less disc space? 
Could i do that without reformating the drives?

---

### Post by TheFu on 2013-11-04
Encrypting data partitions shouldnt be too hard. I have not done this.  There are a few different encryption choices - I would start by looking up **truecrypt**.

Encrypting the entire OS seems to be more complex. On these forums, Ive seen a few people looking for help.  If you are willing to have /boot unencrypted, but everything else encrypted, that seems very doable and relatively easy.

All of these methods REQUIRE excellent backups and a 100%, solid, backup methodology. If you consider that a failed disk sector can make all the data inaccessible across the entire partition.  Backups are job #1, but those are 100x more important when encrypted data is involved.

I do not know if in-place encryption is an option. No way would I start this without a 100%, positive, know-it-works backup. My data is worth at least that much care. A small power hiccup ... data = gone.

I do encrypt my portable devices ... have not tried to full encrypt my laptops, however.  Just the HOME at this point.

Sorry that I am not much use.

There is another option.  Special HDDs are sold with hardware encryption built-in.  I have never heard of more than one being used on a single machine (might be a BIOS limit?) - read up more at addonics.com  I am positive they sell external drive arrays with FIPS encryption - the OS does not need to know.

---

### Post by oldos2er on 2013-11-04
Moved to General Help.

---

