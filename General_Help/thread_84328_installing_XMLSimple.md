---
title: "installing XML::Simple"
date: 2005-10-30
forum: General Help
---

### Post by w0073r on 2005-10-30
I'm trying to install XML::Simple, so that I can use checkgmail. But, well, it doesn't seem to work:

```

dougal@dougal:~$ sudo perl -MCPAN -e 'install XML::Simple'
CPAN: Storable loaded ok
Going to read /home/dougal/.cpan/Metadata
  Database was generated on Sat, 29 Oct 2005 22:00:41 GMT
Running install for module XML::Simple
Running make for G/GR/GRANTM/XML-Simple-2.14.tar.gz
CPAN: Digest::MD5 loaded ok
CPAN: Compress::Zlib loaded ok
Checksum for /home/dougal/.cpan/sources/authors/id/G/GR/GRANTM/XML-Simple-2.14.tar.gz ok
Scanning cache /home/dougal/.cpan/build for sizes
XML-Simple-2.14/
XML-Simple-2.14/t/
XML-Simple-2.14/t/1_XMLin.xml
XML-Simple-2.14/t/lib/
XML-Simple-2.14/t/lib/TagsToUpper.pm
XML-Simple-2.14/t/6_ObjIntf.t
XML-Simple-2.14/t/1_XMLin.t
XML-Simple-2.14/t/srt.xml
XML-Simple-2.14/t/4_MemShare.t
XML-Simple-2.14/t/3_Storable.t
XML-Simple-2.14/t/7_SaxStuff.t
XML-Simple-2.14/t/A_XMLParser.t
XML-Simple-2.14/t/0_Config.t
XML-Simple-2.14/t/subdir/
XML-Simple-2.14/t/subdir/test2.xml
XML-Simple-2.14/t/2_XMLout.t
XML-Simple-2.14/t/5_MemCopy.t
XML-Simple-2.14/t/8_Namespaces.t
XML-Simple-2.14/t/test1.xml
XML-Simple-2.14/t/desertnet.src
XML-Simple-2.14/t/9_Strict.t
XML-Simple-2.14/Changes
XML-Simple-2.14/MANIFEST
XML-Simple-2.14/lib/
XML-Simple-2.14/lib/XML/
XML-Simple-2.14/lib/XML/Simple/
XML-Simple-2.14/lib/XML/Simple/FAQ.pod
XML-Simple-2.14/lib/XML/Simple.pm
XML-Simple-2.14/META.yml
XML-Simple-2.14/maketest
XML-Simple-2.14/README
XML-Simple-2.14/Makefile.PL
Removing previously used /home/dougal/.cpan/build/XML-Simple-2.14

  CPAN.pm: Going to build G/GR/GRANTM/XML-Simple-2.14.tar.gz

Checking installed modules ...
XML::SAX is installed, it will be used by the test suite
Checking if your kit is complete...
Looks good
Writing Makefile for XML::Simple
cp lib/XML/Simple/FAQ.pod blib/lib/XML/Simple/FAQ.pod
cp lib/XML/Simple.pm blib/lib/XML/Simple.pm
Manifying blib/man3/XML::Simple::FAQ.3pm
Manifying blib/man3/XML::Simple.3pm
  /usr/bin/make  -- OK
Running make test
PERL_DL_NONLAZY=1 /usr/bin/perl "-MExtUtils::Command::MM" "-e" "test_harness(0, 'blib/lib', 'blib/arch')" t/*.t
# Package                        Version
#  perl                           5.8.7
#  XML::Simple                    2.14
#  Storable                       2.13
#  XML::Parser                    2.34
#  XML::SAX                       0.13
#  XML::NamespaceSupport          1.09
#  XML::SAX::PurePerl             0.90 (default parser)
t/0_Config........ok
t/1_XMLin.........ok 1/122Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 32
#     Failed test (t/1_XMLin.t at line 380)
#          got: 'Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
# '
#     expected: ''
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/1_XMLin.........NOK 38
#     Failed test (t/1_XMLin.t at line 426)
#     Structures begin differing at:
#          $got->{cdata} = '<greeting>Hello, world!</greeting>>'
#     $expected->{cdata} = '<greeting>Hello, world!</greeting>'
t/1_XMLin.........NOK 39
#     Failed test (t/1_XMLin.t at line 432)
#     Structures begin differing at:
#          $got->{x} = '<y>one</y>><y>two</y>>'
#     $expected->{x} = '<y>one</y><y>two</y>'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96, <STDIN> line 1.
t/1_XMLin.........NOK 122
#     Failed test (t/1_XMLin.t at line 1443)
#     Structures begin differing at:
#          $got->{pubpath}{test1}{title} = 'web_source -> web_target1'
#     $expected->{pubpath}{test1}{title} = 'web_source -&gt; web_target1'
# Looks like you failed 4 tests of 122.
t/1_XMLin.........dubious
        Test returned status 4 (wstat 1024, 0x400)
DIED. FAILED tests 32, 38-39, 122
        Failed 4/122 tests, 96.72% okay
t/2_XMLout........NOK 47
#     Failed test (t/2_XMLout.t at line 302)
#     Structures begin differing at:
#          $got->{c} = '&amp;C&amp;'
#     $expected->{c} = '&C&'
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/2_XMLout........ok 196/196# Looks like you failed 1 test of 196.
t/2_XMLout........dubious
        Test returned status 1 (wstat 256, 0x100)
DIED. FAILED test 47
        Failed 1/196 tests, 99.49% okay (less 1 skipped test: 194 okay, 98.98%)
t/3_Storable......ok
t/4_MemShare......ok
t/5_MemCopy.......ok
t/6_ObjIntf.......ok
t/7_SaxStuff......ok
t/8_Namespaces....ok
t/9_Strict........ok 1/38Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
Unable to recognise encoding of this document at /usr/local/share/perl/5.8.7/XML/SAX/PurePerl/EncodingDetect.pm line 96.
t/9_Strict........ok
t/A_XMLParser.....ok
Failed Test  Stat Wstat Total Fail  Failed  List of Failed
-------------------------------------------------------------------------------
t/1_XMLin.t     4  1024   122    4   3.28%  32 38-39 122
t/2_XMLout.t    1   256   196    1   0.51%  47
1 subtest skipped.
Failed 2/11 test scripts, 81.82% okay. 5/468 subtests failed, 98.93% okay.
make: *** [test_dynamic] Error 255
  /usr/bin/make test -- NOT OK
Running make install
  make test had returned bad status, won't install without force

```

It also seems to be in the libxml-simple-perl package, but that doesn't work: it requires libxml-sax-perl, which won't install.

```
dougal@dougal:~$ sudo apt-get install libxml-sax-perl
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  libxml-sax-perl
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/79.5kB of archives.
After unpacking 446kB of additional disk space will be used.

Preconfiguring packages ...
Selecting previously deselected package libxml-sax-perl.
(Reading database ... 93384 files and directories currently installed.)
Unpacking libxml-sax-perl (from .../libxml-sax-perl_0.12-5_all.deb) ...
Setting up libxml-sax-perl (0.12-5) ...
Can't locate object method "save_parsers_debian" via package "XML::SAX" at /usr/bin/update-perl-sax-parsers line 90.
dpkg: error processing libxml-sax-perl (--configure):
 subprocess post-installation script returned error exit status 255
Errors were encountered while processing:
 libxml-sax-perl
E: Sub-process /usr/bin/dpkg returned an error code (1)
dougal@dougal:~$

```

(Same results on installing libxml-sax-perl if I try to do it by installing libxml-simple-perl.)

Any thought? Thanks.

---

### Post by stoffe on 2005-10-31
Well, it fails the tests due to some encoding error - what is causing it I can't say, why would the documents be in an unrecognized format? Especially since they come with the package... sounds weird.

libxml-simple-perl installed here without a glitch, including the sax package, so I can't help you with reproducing... it points to something broken on your end what with the strange errors too.

However, since it's failed tests, you might be able to install the via CPAN anyways, by forcing the install to happen. If it's only the tests, this should be fine. However, if the failing tests indicate worse problems with the package or your system (that's why they are there) you might be in trouble. So think it through first...

perl -MCPAN -e shell
cpan> force install XML::Simple

---

### Post by w0073r on 2005-10-31
Okay, well that worked...

Thanks.

---

### Post by hugin0 on 2005-11-11
well i'm getting the same error, and i would like to figure out why it is happening, rather than forcing a package.  if anyone has any ideas please help.


/jhs

---

### Post by bugardifieno on 2006-07-20
There is an answer at this address.
[http://rt.cpan.org/Public/Bug/Display.html?id=15345](http://rt.cpan.org/Public/Bug/Display.html?id=15345)

This site said that "the parser is broken" which I gather means it can't read the file. I had the same problem, installed XML::SAX::Expat and then XML::Simple installed properly.

---

### Post by Dewni on 2007-07-04
I found this error while mucking about on my debian server. Looking around gave me this solution:

from [http://wereldmuis.blogspot.com/](http://wereldmuis.blogspot.com/)

/usr/share/perl5 is in the list but it is preceded by other directories, some of which contain a different version of XML::SAX

I am quoting his blog, just because of the volatility of some blogs.... Noting but respect for this linuxmancer ;)



> Ack! Something bad happened while installing packages...
To get more info:

```
aptitude search libxml|grep perl
...
u A libxml-libxml-perl - Perl module for using the GNOME libxml2 li
...
C A libxml-sax-perl - Perl module for using and building Perl SA
...
u libxml-simple-perl - Perl module for reading and writing XML
```

The "u" means "unpacked but not configured". The "C" means "half-configured: the package's configuration was interrupted". The "A" means "automatically installed". This turned out to be a red herring though. The problem was that there are several versions of XML::SAX only one of which has the required save_parsers_debian method:

```
find / -name SAX.pm -exec grep -H 'save_parsers_debian' {} \;
/usr/share/perl5/XML/SAX.pm:sub save_parsers_debian {
```


So clearly the perl path, determined by @INC, does not point to the version of SAX.pm which we need. Let's see what it is. Create a file sniff.pl which contains an error:

```
#!/usr/bin/perl
use sniff; # a non-existent package, so that perl will print @INC
```

and run it

```
perl sniff.pl
Can't locate sniff.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at sniff.pl line 2
```.

Ah, /usr/share/perl5 is in the list but it is preceded by other directories, some of which contain a different version of XML::SAX. Let's promote it to the top of the path:

```
export PERL5LIB=/usr/share/perl5/
perl sniff.pl
Can't locate sniff.pm in @INC (@INC contains: /usr/share/perl5/ /etc/perl /usr/local/lib/perl/5.8.4 /usr/local/share/perl/5.8.4 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at sniff.pl line 2.
```

Notice how the path has changed.

This solved my apt-get errors.

---

