---
title: "perl script stopped working?"
date: 2007-04-03
forum: General Help
---

### Post by kasper22 on 2007-04-03
Hi Everyone,

I'm having a strange issue,  I wrote a perl script that uses the CDDB_get perl module and it worked fine for month and even last week.  Today I went to use it and I'm getting this error:
> Odd number of elements in hash assignment at ./music_ripper line 22.
Use of uninitialized value in list assignment at ./music_ripper line 22.
no cddb entry found at ./music_ripper line 25.


Here is the script that I'm using:
```
#!/usr/bin/perl -w 

	use CDDB_get qw( get_cddb );

        my %config;

        # following variables just need to be declared if different from defaults

        $config{CDDB_HOST}="freedb.freedb.org";        # set cddb host
        $config{CDDB_PORT}=8880;                       # set cddb port
        $config{CDDB_MODE}="cddb";                     # set cddb mode: cddb or http
        $config{CD_DEVICE}="/dev/cdrom";               # set cd device

        # user interaction welcome?

        $config{input}=1;   # 1: ask user if more than one possibility
                            # 0: no user interaction

        # get it on

        my %cd=get_cddb(\%config);

        unless(defined $cd{title}) {
          die "no cddb entry found";
        }

        # do somthing with the results

        print "artist: $cd{artist}\n";
        print "title: $cd{title}\n";
        print "category: $cd{cat}\n";
        print "cddbid: $cd{id}\n";
        print "trackno: $cd{tno}\n";

        my $n=1;
        foreach my $i ( @{$cd{track}} ) {
          print "track $n: $i\n";
          $n++;
        }

```
Anyone have an idea why it would start giving such a strange message.  (strange since the code worked fine before and now it's saying I have a hash pair that is not set up).

Thanks
Bryan

---

