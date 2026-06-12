---
title: "SQL Server"
date: 2008-02-20
forum: General Help
---

### Post by EvilMarshmallow on 2008-02-20
Hey all,

I'm working on a project that involves a computer on our plant floor receiving a Comma-separated text file of values from a scale system and depositing it in a SQL Server Database.  I'd like to minimize my expense, so not buying a Windows license would really help out.  

Basically I'm going to have a directory that receives a series of files with timestamps for names.  Then every 5 minutes, a program should run (probably a cron job) that will read all the records entered since the last run and write them to the SQL DB on my server.

What's the best way to communicate from Ubuntu to a SQL Server?

---

### Post by SoggyCornflake on 2008-02-20
> **EvilMarshmallow said:**
> What's the best way to communicate from Ubuntu to a SQL Server?

I've not tried these but ubuntu pakages included **[sqlrelay-freetds]("http://packages.ubuntu.com/gutsy/sqlrelay-freetds")**.  **[sqsh]("http://packages.ubuntu.com/gutsy/sqsh")**, & [**freetds-dev**]("http://packages.ubuntu.com/gutsy/freetds-dev").

Hopefully one of those would work.  Good Luck.

---

### Post by tlacuache on 2008-02-20
I've used perl's DBI module (which uses FreeTDS) to do just that.

```
#!/usr/bin/perl

use DBI;

my $user   = 'username';
my $passwd = 'password';

my $dbh = DBI->connect("DBI:Sybase:server=ServerName", $user, $passwd, {PrintError => 0});

unless ($dbh) {
  print "Unable for connect to server $DBI::errstr\n";
  exit(1);
}

my $sqlQuery = "SELECT COUNT(*) FROM Database..Table";
print "Executing query...\n";
my $tableQuery = $dbh->prepare($sqlQuery);
if ($tableQuery->execute) {
    while(@dat = $tableQuery->fetchrow) {
      print "\t@dat\n";
    }
} else {
  print "Could not execute query: $DBI::errstr\n";
  exit(1);
}

exit(0);
```

FreeTDS defines what a database is in /etc/freetds/freetds.conf. For the above connection, my file looks like this:

```

[ServerName]
host = 10.0.2.35
port = 1433
tds version = 4.2

```

The name (what's in the square brackets) really doesn't matter, it's just what you use to reference the server in your perl script.

Good luck,

-SG

---

