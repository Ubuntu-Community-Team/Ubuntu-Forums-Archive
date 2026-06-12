---
title: "OpenOffice database form problem"
date: 2008-03-22
forum: General Help
---

### Post by bkline on 2008-03-22
Anyone else seen this problem?  I've hooked up OpenOffice Base to a mysql database, and used the wizard to create a form on one of the tables.  When I use the form to enter a new row I get an error dialog which says 

    Error inserting the new record

    [MySQL[pODBC 3.51 Driver][mysqldb-5.0.32-Debian_7etch5-
    log]Column 'Amount' cannot be null

The form has a field for Amount, and it's bound to the Amount column in the database, and I've entered a valid value into the field.

This is on Gutsy, using openoffice.org-base 1:2.3.0-1ubuntu5.3.

---

