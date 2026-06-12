---
title: "Has docker support of grep commands?"
date: 2021-10-02
forum: General Help
---

### Post by petrogromovo on 2021-10-02
Hello,
I want in docker(based FROM php:7.4-apache) to support of commands which I use in ubuntu :

```
    locate filename

```
and 

```
    grep -Hrn  -A 5 'search text' --include="*.php"  /DirectoryPath/

```

After adding command in my Dockerfile.yml 

```
    RUN apt-get install -y grep mlocate

```
I can run command :

```
    grep -Hrn  -A 5 'var' --include="*.conf"  /var/www

```
with valid results, but errors with locate :

```
    root@11ed27f97ac4:/var/www# locate -help
    Usage: locate [OPTION]... [PATTERN]...
    Search for entries in a mlocate database.
    
      -A, --all              only print entries that match all patterns
      -b, --basename         match only the base name of path names
      -c, --count            only print number of found entries
      -d, --database DBPATH  use DBPATH instead of default database (which is
                             /var/lib/mlocate/mlocate.db)
      -e, --existing         only print entries for currently existing files
      -L, --follow           follow trailing symbolic links when checking file
                             existence (default)
      -h, --help             print this help
      -i, --ignore-case      ignore case distinctions when matching patterns
      -l, --limit, -n LIMIT  limit output (or counting) to LIMIT entries
      -m, --mmap             ignored, for backward compatibility
      -P, --nofollow, -H     don't follow trailing symbolic links when checking file
                             existence
      -0, --null             separate entries with NUL on output
      -S, --statistics       don't search for entries, print statistics about each
                             used database
      -q, --quiet            report no error messages about reading databases
      -r, --regexp REGEXP    search for basic regexp REGEXP instead of patterns
          --regex            patterns are extended regexps
      -s, --stdio            ignored, for backward compatibility
      -V, --version          print version information
      -w, --wholename        match whole path name (default)
    
    Report bugs to mitr@redhat.com.
    root@11d2e77af9c4:/var/www# mlocate -i error.log 
    mlocate: can not stat () `/var/lib/mlocate/mlocate.db': No such file or directory

```
Why error at last line ? Seems I use valid syntax ?

Thanks in advance!

---

