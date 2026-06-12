---
title: "Fluxbox xsession errors"
date: 2006-07-18
forum: General Help
---

### Post by ScreemingBlue on 2006-07-18
I am using fluxbox in Dapper from the repos and I get > Warning: Failed to open file(/usr/share/fluxbox/nls/en_GB/fluxbox.cat)
for translation, using default messages. in my xsession.errors file.

Funny because en_GB is my default language setting. For some reason the file doesn't even exist, see here.. > ls /usr/share/fluxbox/nls/
be_BY/ cs_CZ/ el_GR/ fr_FR/ ko_KR/ pl_PL/ ru_RU/ tr_TR/ 
bg_BG/ da_DK/ es_ES/ it_IT/ lv_LV/ pt_BR/ sl_SI/ uk_UA/ 
C/     de_DE/ et_EE/ ja_JP/ nl_NL/ pt_PT/ sv_SE/ vi_VN/ 

Any ideas.

---

### Post by lex1 on 2006-07-18
i get the same thing but still fluxbox appears ok


lex1

---

### Post by ScreemingBlue on 2006-07-18
Are you using fluxbox from the repos or form source?

---

### Post by ScreemingBlue on 2006-07-18
I am going to try and compile from source and see what changes..keep you posted.

---

