---
title: "Strange Error When Changing Software Update Setting 24.10"
date: 2024-10-15
forum: General Help
---

### Post by kauxier94 on 2024-10-15
I get this error message when trying to change settings in the software updater. I have yet to receive any updates since switching over to 24.10, so I am not sure if it is working correctly. Thank you for any help you can provide.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294367&stc=1[/IMG]

---

### Post by guiverc on 2024-10-16
I see a number of errors..  but as you've provided a picture of text (*not text that I can copy & look up actual details, then paste results** here*) I'll only provide some.

- I note mention of ESM, a service provided by Canonical for LTS releases only; but 24.10 is NOT a LTS thus isn't supported by ESM, thus issues relating to ESM are to be expected; you should remove your ESM, or restore your backup so you're re-using 24.04 where ESM is available.

You can confirm this using 

```

ubuntu-security-status

```

which tells me a number of things, and includes the message

```

Ubuntu Pro is not available for non-LTS releases

```

where ESM & Pro are offered only for LTS so the same applies.

I've noticed only a single upgrade since 24.10's release on my install, and that was a third-party browser I have installed from a non-Ubuntu repository; I've got nothing myself from Ubuntu, but I'm not expecting anything either yet.

Your using Lubuntu (*where you posted this question*) doesn't change any rules in regards Ubuntu repositories than if using a Ubuntu Desktop/Server system.

---

### Post by grahammechanical on 2024-10-16
The other repository mentioned is Winehq. Open Software and Updates>Other Software and disable the winehq.org repository. That error message will disappear. What version of Ubuntu were you using when you installed Wine? There is not yet a version of Wine for 24.10.

Normally, when we do an online upgrade the internet addresses for third party repositories are changed to match the code name of the new release we are upgrading to. In your case it is oracular. And because wine does not have an oracular repository the installer cannot transition the internet addresses. So, we get error messages. By the way, the internet addresses for Ubuntu repositories (software sources) are also changed in the same way.

Regards

---

