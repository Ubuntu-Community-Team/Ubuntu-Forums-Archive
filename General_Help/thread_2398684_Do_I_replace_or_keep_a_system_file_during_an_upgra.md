---
title: "Do I replace or keep a system file during an upgrade"
date: 2018-08-15
forum: General Help
---

### Post by waltd on 2018-08-15
When I upgrade Ubuntu I'm always asked "do I want to replace a system file or keep the existing one". I don't know the bestg answer.  I usually replace the file, however what is the best decision?  When I'm asked, should I replace the system files or keep the existing ones.

---

### Post by DuckHook on 2018-08-15
You are usually asked this question only in those cases where you had customized a configuration file in the last version. If you remember having done so, you may not wish to have it replaced with a new default file because you will lose all of your customizations. This is most often the case with a customized GRUB file. Since there is not much change from one GRUB version to the next, it is usually best to keep the old GRUB file.

This is a common issue, especially with newer users, and it's a shame that the warning message cannot be more descriptive. Usually, when this choice pops up, there is also an option to compare the two files. If you are comfortable with the command line, this is often a good option.

---

### Post by echotech2 on 2018-08-17
Their should be a third button labelled "Maybe"

---

