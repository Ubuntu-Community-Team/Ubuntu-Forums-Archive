---
title: "uninstalling Berkeley 4.8 after compiling from source?"
date: 2014-01-14
forum: General Help
---

### Post by merockstar on 2014-01-14
I'm such a noob.

I was trying to make something work. And Berekeley 4.8 was a dependency according the readme.

So I downloaded it from here

[http://www.oracle.com/technetwork/database/database-technologies/berkeleydb/downloads/index-082944.html](http://www.oracle.com/technetwork/database/database-technologies/berkeleydb/downloads/index-082944.html)

and compiled from source using the following instructions:

```
Berkeley DB
-----------
You need Berkeley DB 4.8.  If you have to build Berkeley DB yourself:
../dist/configure --enable-cxx
make

```

Later, I came to realize that this was not at all the problem, and that I need to use the libdb++ repo.

so when i sudo apt-get install libdb++ I get:

```
merockstar@merockstar-HP-Pavilion-dv6-Notebook-PC:~/devcoin-devcoin$ sudo apt-get install libdb++
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libdb5.1-java-dev' for regex 'libdb+'
Note, selecting 'libdbusmenu-qt2' for regex 'libdb+'
Note, selecting 'libdbix-class-datetime-epoch-perl' for regex 'libdb+'
Note, selecting 'libdb5.1-sql' for regex 'libdb+'
Note, selecting 'libdbus-glib-dev' for regex 'libdb+'
Note, selecting 'libdbd-sqlite3-ruby1.9.1' for regex 'libdb+'
Note, selecting 'libdb5.1-stl' for regex 'libdb+'
Note, selecting 'libdb5.1-java-gcj' for regex 'libdb+'
Note, selecting 'libdb4.6-tcl' for regex 'libdb+'
Note, selecting 'libdbd-pg-ruby' for regex 'libdb+'
Note, selecting 'libdbix-recordset-perl' for regex 'libdb+'
Note, selecting 'libdb-je-java' for regex 'libdb+'
Note, selecting 'libdballef-dev' for regex 'libdb+'
Note, selecting 'libdb5.1++-dev' for regex 'libdb+'
Note, selecting 'libdbd-sqlite3-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbix-connector-perl' for regex 'libdb+'
Note, selecting 'libdbd-odbc-ruby' for regex 'libdb+'
Note, selecting 'libdb2-dev' for regex 'libdb+'
Note, selecting 'libdbd-firebird-perl' for regex 'libdb+'
Note, selecting 'libdbd-csv-perl' for regex 'libdb+'
Note, selecting 'libdbi0-dev' for regex 'libdb+'
Note, selecting 'libdbix-dbschema-perl' for regex 'libdb+'
Note, selecting 'libdb5.1-sql-dev' for regex 'libdb+'
Note, selecting 'libdbus-ocaml-dev-2rv18' for regex 'libdb+'
Note, selecting 'libdbus1.0-cil-dev' for regex 'libdb+'
Note, selecting 'libdbd-pgsql' for regex 'libdb+'
Note, selecting 'libdbix-xml-rdb-perl' for regex 'libdb+'
Note, selecting 'libdb4.7-java-dev' for regex 'libdb+'
Note, selecting 'libdbix-datasource-perl' for regex 'libdb+'
Note, selecting 'libdb4.7-dev' for regex 'libdb+'
Note, selecting 'libdbix-contextualfetch-perl' for regex 'libdb+'
Note, selecting 'libdb-sql-dev' for regex 'libdb+'
Note, selecting 'libdb++-dev' for regex 'libdb+'
Note, selecting 'libdbix-profile-perl' for regex 'libdb+'
Note, selecting 'libdbd-oracle-perl' for regex 'libdb+'
Note, selecting 'libdbix-class-inflatecolumn-ip-perl' for regex 'libdb+'
Note, selecting 'libdballe-db-dev' for regex 'libdb+'
Note, selecting 'libdbus-1-3' for regex 'libdb+'
Note, selecting 'libdb-file-lock-perl' for regex 'libdb+'
Note, selecting 'libdbus-java' for regex 'libdb+'
Note, selecting 'libdb-java' for regex 'libdb+'
Note, selecting 'libdbus-glib-1-2' for regex 'libdb+'
Note, selecting 'libdbi-perl' for regex 'libdb+'
Note, selecting 'libdbix-password-perl' for regex 'libdb+'
Note, selecting 'libdb-java-dev' for regex 'libdb+'
Note, selecting 'libdb5.1++' for regex 'libdb+'
Note, selecting 'libdbi0' for regex 'libdb+'
Note, selecting 'libdbi1' for regex 'libdb+'
Note, selecting 'libdbd-informix-perl' for regex 'libdb+'
Note, selecting 'libdbd-sqlite3-perl' for regex 'libdb+'
Note, selecting 'libdb4.6-java-dev' for regex 'libdb+'
Note, selecting 'libdbd-mysql' for regex 'libdb+'
Note, selecting 'libdb4.7-tcl' for regex 'libdb+'
Note, selecting 'libdb4o7.4-cil' for regex 'libdb+'
Note, selecting 'libdb4.4-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbm-deep-perl' for regex 'libdb+'
Note, selecting 'libdbicx-testdatabase-perl' for regex 'libdb+'
Note, selecting 'libdbd-mysql-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbus1.0-cil' for regex 'libdb+'
Note, selecting 'libdbix-class-htmlwidget-perl' for regex 'libdb+'
Note, selecting 'libdbm-ruby1.8' for regex 'libdb+'
Note, selecting 'libdb-dev' for regex 'libdb+'
Note, selecting 'libdb3-dev' for regex 'libdb+'
Note, selecting 'libdbix-dbstag-perl' for regex 'libdb+'
Note, selecting 'libdb1-compat' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk-dev' for regex 'libdb+'
Note, selecting 'libdbd-msql-perl' for regex 'libdb+'
Note, selecting 'libdb5.1-java' for regex 'libdb+'
Note, selecting 'libdb4.7++-dev' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk-doc' for regex 'libdb+'
Note, selecting 'libdballe-msg-dev' for regex 'libdb+'
Note, selecting 'libdb4.8-dev' for regex 'libdb+'
Note, selecting 'libdbm-ruby1.9.1' for regex 'libdb+'
Note, selecting 'libdbix-easy-perl' for regex 'libdb+'
Note, selecting 'libdb-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbd-mock-perl' for regex 'libdb+'
Note, selecting 'libdbus-c++-dbg' for regex 'libdb+'
Note, selecting 'libdballe-bufrex-dev' for regex 'libdb+'
Note, selecting 'libdbus-c++-dev' for regex 'libdb+'
Note, selecting 'libdbm-ruby' for regex 'libdb+'
Note, selecting 'libdballe-core-dev' for regex 'libdb+'
Note, selecting 'libdbus-c++-doc' for regex 'libdb+'
Note, selecting 'libdbi-dev' for regex 'libdb+'
Note, selecting 'libdbi-doc' for regex 'libdb+'
Note, selecting 'libdbd-anydata-perl' for regex 'libdb+'
Note, selecting 'libdbd-odbc-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbd-sqlite3' for regex 'libdb+'
Note, selecting 'libdbi-ruby' for regex 'libdb+'
Note, selecting 'libdbusmenu-glib0' for regex 'libdb+'
Note, selecting 'libdbusmenu-glib1' for regex 'libdb+'
Note, selecting 'libdbusmenu-glib4' for regex 'libdb+'
Note, selecting 'libdbusmenu-jsonloader-dev' for regex 'libdb+'
Note, selecting 'libdbus-glib1.0-cil' for regex 'libdb+'
Note, selecting 'libdbusmenu-qt-dev' for regex 'libdb+'
Note, selecting 'libdbd-pg-ruby1.9.1' for regex 'libdb+'
Note, selecting 'libdbix-simple-perl' for regex 'libdb+'
Note, selecting 'libdbusmenu-qt-doc' for regex 'libdb+'
Note, selecting 'libdbus-ocaml' for regex 'libdb+'
Note, selecting 'libdbix-class-timestamp-perl' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk3-dev' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk1' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk4' for regex 'libdb+'
Note, selecting 'libdbd-sqlite3-ruby' for regex 'libdb+'
Note, selecting 'libdbusmenu-gtk3-4' for regex 'libdb+'
Note, selecting 'libdb5.1-stl-dev' for regex 'libdb+'
Note, selecting 'libdb4o-cil-dev' for regex 'libdb+'
Note, selecting 'libdb4o8.0-cil' for regex 'libdb+'
Note, selecting 'libdbus-ocaml-2rv18' for regex 'libdb+'
Note, selecting 'libdbusmenu-jsonloader4' for regex 'libdb+'
Note, selecting 'libdb4.2-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbd-mysql-perl' for regex 'libdb+'
Note, selecting 'happycoders-libdbg' for regex 'libdb+'
Note, selecting 'libdbix-class-introspectablem2m-perl' for regex 'libdb+'
Note, selecting 'libdb4.8-tcl' for regex 'libdb+'
Note, selecting 'libdbd-ldap-perl' for regex 'libdb+'
Note, selecting 'libdb4.2-dev' for regex 'libdb+'
Note, selecting 'libdbix-xmlmessage-perl' for regex 'libdb+'
Note, selecting 'libdballe-dev' for regex 'libdb+'
Note, selecting 'libdbd-mysql-5.1-perl' for regex 'libdb+'
Note, selecting 'libdbix-class-cursor-cached-perl' for regex 'libdb+'
Note, selecting 'libdballe-doc' for regex 'libdb+'
Note, selecting 'libdb4o6.0-cil' for regex 'libdb+'
Note, selecting 'libdbus-glib0-dev' for regex 'libdb+'
Note, selecting 'libdb2-util' for regex 'libdb+'
Note, selecting 'libdbd-sqlite' for regex 'libdb+'
Note, selecting 'libdbus-c++-1-0' for regex 'libdb+'
Note, selecting 'libdbusmenu-tools' for regex 'libdb+'
Note, selecting 'libdbd-sybase-perl' for regex 'libdb+'
Note, selecting 'libdbix-sequence-perl' for regex 'libdb+'
Note, selecting 'libdbix-abstract-perl' for regex 'libdb+'
Note, selecting 'libdbd-excel-perl' for regex 'libdb+'
Note, selecting 'libdbus-glib-1-2-dbg' for regex 'libdb+'
Note, selecting 'libdbix-class-encodedcolumn-perl' for regex 'libdb+'
Note, selecting 'libdbd-pg-perl' for regex 'libdb+'
Note, selecting 'libdbi-ruby1.9.1' for regex 'libdb+'
Note, selecting 'libdbix-oo-perl' for regex 'libdb+'
Note, selecting 'libdbd-pg-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbus-ruby1.8' for regex 'libdb+'
Note, selecting 'libdb4.7' for regex 'libdb+'
Note, selecting 'libdb5.1-dbg' for regex 'libdb+'
Note, selecting 'libdb4.8' for regex 'libdb+'
Note, selecting 'libdbd-freetds' for regex 'libdb+'
Note, selecting 'libdb5.1' for regex 'libdb+'
Note, selecting 'libdballef4' for regex 'libdb+'
Note, selecting 'libdbd-odbc-perl' for regex 'libdb+'
Note, selecting 'libdb5.1-dev' for regex 'libdb+'
Note, selecting 'libdbd-sqlite2-perl' for regex 'libdb+'
Note, selecting 'libdbus-ocaml-dev' for regex 'libdb+'
Note, selecting 'libdbix-searchbuilder-perl' for regex 'libdb+'
Note, selecting 'libdb4.6-dev' for regex 'libdb+'
Note, selecting 'libdbd-mysql-ruby1.9.1' for regex 'libdb+'
Note, selecting 'libdbix-safe-perl' for regex 'libdb+'
Note, selecting 'libdb4.8++-dev' for regex 'libdb+'
Note, selecting 'libdbix-fulltextsearch-perl' for regex 'libdb+'
Note, selecting 'libdbus-1-dev' for regex 'libdb+'
Note, selecting 'libdbix-class-candy-perl' for regex 'libdb+'
Note, selecting 'libdbd-mysql-ruby' for regex 'libdb+'
Note, selecting 'libdb4o-doc' for regex 'libdb+'
Note, selecting 'libdbd-xbase-perl' for regex 'libdb+'
Note, selecting 'happycoders-libdbg-dev' for regex 'libdb+'
Note, selecting 'libdbus-ruby' for regex 'libdb+'
Note, selecting 'libdbi-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbi-ruby1.9' for regex 'libdb+'
Note, selecting 'libdbus-glib1.0-cil-dev' for regex 'libdb+'
Note, selecting 'libdbus-glib-1-dev' for regex 'libdb+'
Note, selecting 'libdbus-glib-1-doc' for regex 'libdb+'
Note, selecting 'libdbus-java-doc' for regex 'libdb+'
Note, selecting 'libdballe5' for regex 'libdb+'
Note, selecting 'libdbix-class-schema-loader-perl' for regex 'libdb+'
Note, selecting 'libdbix-class-tree-nestedset-perl' for regex 'libdb+'
Note, selecting 'libdb4.6++-dev' for regex 'libdb+'
Note, selecting 'libdbix-class-perl' for regex 'libdb+'
Note, selecting 'libdb4.3-ruby1.8' for regex 'libdb+'
Note, selecting 'libdbusmenu-glib-dev' for regex 'libdb+'
Note, selecting 'libdbix-class-dynamicdefault-perl' for regex 'libdb+'
Note, selecting 'libdb4.8-java-dev' for regex 'libdb+'
Note, selecting 'libdb4o6.1-cil' for regex 'libdb+'
Note, selecting 'libdbusmenu-glib-doc' for regex 'libdb+'
Note, selecting 'libdb5.1-tcl' for regex 'libdb+'
Note, selecting 'libdbi-dev' instead of 'libdbi0-dev'
Note, selecting 'libruby' instead of 'libdbm-ruby'
Note, selecting 'libruby1.8' instead of 'libdbm-ruby1.8'
Note, selecting 'libruby1.9.1' instead of 'libdbm-ruby1.9.1'
Note, selecting 'libdbus-ocaml' instead of 'libdbus-ocaml-2rv18'
Note, selecting 'libdbus-ocaml-dev' instead of 'libdbus-ocaml-dev-2rv18'
libdb5.1 is already the newest version.
libdbusmenu-qt2 is already the newest version.
libdbusmenu-qt2 set to manually installed.
libdbus-1-3 is already the newest version.
libdbus-glib-1-2 is already the newest version.
libdbusmenu-glib4 is already the newest version.
libdbusmenu-glib4 set to manually installed.
libdbusmenu-gtk3-4 is already the newest version.
libdbusmenu-gtk4 is already the newest version.
libdbusmenu-gtk4 set to manually installed.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libdb-dev : Conflicts: libdb4.8-dev but 4.8.30-11ubuntu1 is to be installed
 libdb4.8-dev : Conflicts: libdb-dev but 5.1.4ubuntu1 is to be installed
 libdb5.1-dev : Conflicts: libdb4.8-dev but 4.8.30-11ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```

ugh.

is this correctable?

---

### Post by Impavidus on 2014-01-14
The package libdb++ doesn't exist in the Ubuntu repository. You need the package libdb<version>++. Because it doesn't exist, apt-get interprets libdb++ as a regular expression and selects all matching packages. Some of these are conflicting, and therefore apt-get returns an error.

---

