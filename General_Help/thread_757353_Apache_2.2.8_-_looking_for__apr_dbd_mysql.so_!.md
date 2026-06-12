---
title: "Apache 2.2.8 - looking for  apr_dbd_mysql.so !"
date: 2008-04-16
forum: General Help
---

### Post by rycole on 2008-04-16
Hey all,

I've downloaded and installed various packages in relation to apache, and have enabled the modules. I'm trying to setup apache2 so that it authenticates users based on data from a mysql database. I'm using mod_authn_dbd, and mod_dbd. I have specified the documented DBDriver param in the apache config, and it tells me that I do not have the apr_dbd_mysql.so file available. This file is provided with apache's portable runtime library now, but is not compiled by default. I was wondering, is there any package that has this file in it? Or, will I have to manually compiled mysql, and apache, and apache's portable runtime library just for this single file? Any help is appreciated, thank you!

---

### Post by rycole on 2008-04-17
bump

---

### Post by rycole on 2008-04-18
bump

---

### Post by tim_za on 2008-05-28
Hi

Currently, as far as I know, you can't build the dbd drivers as modules loadable like the other apache modules (although I think there is some work in this regard).

So you *aren't* actually looking for that file, what you want is to compile it into apr-util, as you noted.

In order for that to work, you need to have the mysql development package installed (libmysqlclient15-dev) likewise for pgsql you'll need postgresql dev package.
Then from the apache source you compile the srclib/apr-util to include mysql, and install it in the correct location.

APR:

apr-util depends on apr being installed, so I think you'll need to compile / install this first. 
You can try just compiling and installing the apr-util below if you already have an installed apache, provided you get the prefix with-apr values correct, *it should just update you're current installation*.


```

cd srclib/apr
./configure --prefix=/usr/local/apache2
make
sudo make install

```

APR-UTIL:

```
cd srclib/apr-util
./buildconf #I believe this is necessary for the first build
./configure --prefix=/usr/local/apache2 --with-apr=/usr/local/apache2 --with-mysql=/usr/lib/mysql --with-pgsql=/usr/lib/postgresql/8.3 
make
sudo make install

```

(If you want to look at options for the configure command, use ./configure --help)



The --prefix option specifies where to install the libraries (they will be installed to PREFIX/lib - look for libaprutil-1.* there).
The --with-apr option specifies where the apr libraries are installed (it will look in PREFIX/lib for them), they are usually found in the same directory as the aprutil so *the two options should be the same*.


If you're using the standard ubuntu install of apache then you're prefix would be different, but I have only done this using the source which I installed to /usr/local/apache2 so I'm not sure whether it will work for you in that case (if not just install fully from source as described here and uninstall the ubuntu package - remember to backup conf files).

You'll see the configure script looking for the header files for mysql or postgresql, where it should say yes (found) and then there'll be a line or two adding the location to the compiler flags. If it doesn't find the files then it won't complain, you just won't have it compiled in, so be sure to check the output if it's not working.

HTTP:

If you haven't already got an installation of apache then compile and install for the same prefix (all three packages should use the same --prefix location).
When building the apache you'll need to specify --with-apr=/usr/local/apache2 and --with-apr-utils=/usr/local/apache2 (or where ever you installed them to) so that those two don't get recompiled and overwritten.
Specify what ever options you want with the server (like enable-mods-shared=all). You know the rest:
```

./configure --prefix=/usr/local/apache2 --with-apr=/usr/local/apache2 --with-apr-util=/usr/local/apache2 --enable-mods-shared=all
make
sudo make install

```

Then you should be able to use authn_dbd with the database driver of your choice.

Let me know if the above works for you, it has for me, but my setup may have been slightly different to yours (btw I used source code from apache, but you can try ubuntus source package I'm sure it will work).

Oh yes, and if you're looking at the apache docs for setting up the mod_dbd then you'll want to change 'password' in the line
	DBDParams "dbname=database user=username password=xxx"
to 'pass' for it to work with mysql.

All that said...there's nothing wrong with PostgreSQL so if that comes standard with the ubuntu package then think about installing that database if you're server has it or allows you to install it.

Tim

---

