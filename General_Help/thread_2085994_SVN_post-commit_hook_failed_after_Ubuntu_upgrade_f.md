---
title: "SVN post-commit hook failed after Ubuntu upgrade from 11.04 to 12.04"
date: 2012-11-19
forum: General Help
---

### Post by JackTheKnife on 2012-11-19
After Ubuntu upgrade from 11.04 to 12.04 all my SVN post-commit hooks doesn't work throwing errors:

```
post-commit hook failed (exit code 1) with output:
sudo: no tty present and no askpass program specified

```

Any clue what can be wrong?

---

### Post by JackTheKnife on 2012-11-21
More info regarding that issue.

Error comes on TortoiseSVN.

My post-commit hook looks like:

```
sudo svn update /var/www/site/html >> /usr/local/svn/repos/site/logs/exampleup.log
```

and working sudoers from 11.04:
```

www-data ALL=NOPASSWD:/usr/bin/svn
```

---

