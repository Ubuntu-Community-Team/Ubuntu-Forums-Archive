---
title: "libgda with unixODBC"
date: 2006-10-02
forum: General Help
---

### Post by Macuyiko on 2006-10-02
I want to use Mergeant with my odbc database, I've already set up the unixODBC driver and namespace (isql works) but since Mergeant relies on gnome-db (libgda) I was wondering how to get this to work.

Probably by setting up /etc/libgda/config but I don't know how (the documentation also doesn't give any guidelines, other than: use the dsn you would give to your odbc manager). Also, my only libgda provider at the moment is the default XML one, maybe I first need to install a unixodbc-wrapper-provider?

Can anyone help? Thanks.

---

### Post by Macuyiko on 2006-10-02
Whoops, that was stupid, figured out I needed 'gda2-odbc'. Then just use your unixODBC namespace name as connection string.

(Also I had to:
export ODBCINI=/etc/odbc.ini
export ODBCINSTINI=/etc/odbcinst.ini
but that might be because I messed around a bit.)

---

