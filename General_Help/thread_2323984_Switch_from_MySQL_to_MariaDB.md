---
title: "Switch from MySQL to MariaDB"
date: 2016-05-09
forum: General Help
---

### Post by SchnappiJedi on 2016-05-09
Hello,

Would like to move all servers from MySQL to MariaDB. Some people say remove MySQL first while other says just install MariaDB and it will basically just upgrade MySQL to MariaDB.

What says everyone here? Can one just run "sudo apt-get install mariadb-server" and be done?

---

### Post by nerdtron on 2016-05-10
I don't think that will work. MariaDB is an in-place replacement for mysql. The config files in /etc/ and the database files on /var/lib/mysql are the same file names used by mariaDB and mySQL. It's all basically a conflict.

Why don't you just export your MySQL database and then import it to MariaDB. If they have they same version, there should be no problems.

---

### Post by SchnappiJedi on 2016-05-18
Does anyone know of a good upgrade tutorial from MySQL to MariaDB?

---

