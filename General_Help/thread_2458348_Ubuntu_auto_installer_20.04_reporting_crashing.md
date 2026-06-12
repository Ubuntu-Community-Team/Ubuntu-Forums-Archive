---
title: "Ubuntu auto installer 20.04 reporting crashing"
date: 2021-02-22
forum: General Help
---

### Post by kmolnar2 on 2021-02-22
Hello,

I am currently facing a problem with the ubuntu auto installer (20.04.02 LTS). (The image is the daily image from 20210201) There is an option referenced in the references for disabling output on (tty1) during the boot/install process. The purpose would be a kiosk style "no output visible" automated installation.

Link to the documentation: [https://ubuntu.com/server/docs/install/autoinstall-reference](https://ubuntu.com/server/docs/install/autoinstall-reference)

```

reporting:
  builtin:
    type: none

```

As far as I understood this piece of code would be responsible for inhibiting output but for me the installer just crashes. I tried type: print, and that one works as expected, so I am sure that the structure is alright. I do not have interactive sections.

Here is the error: [ATTACH=CONFIG]287996[/ATTACH]

---

