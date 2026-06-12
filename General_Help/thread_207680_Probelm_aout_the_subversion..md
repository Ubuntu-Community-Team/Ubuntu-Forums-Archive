---
title: "Probelm aout the subversion."
date: 2006-07-02
forum: General Help
---

### Post by flying_eagle2003 on 2006-07-02
Hi all:

I'm struggling to resolve a problem about accessing the subversion repository by HTTP. To achieve the purpose, I added the following into the apache2.conf:
<Location /test_lzr>
DAV svn
SVNPath /home/svn/mypp
AuthType Basic
AuthName "my project test"
AuthUserFile /etc/subversion/passwd
<LimitExcept GET PROPFIND OPTIONS REPORT>
Require valid-user
</LimitExcept>
</Location>

Then added a user 'xxx' to the /etc/subversion/passwd file.
It worked better while I test it using the following command:
svn co [http://server/svn](http://server/svn) mypp --username xxx.

In order to support the muti-project easily, I changed the configuration as the following:
<Location /test_lzr>
DAV svn
SVNParentPath /home/svn
AuthType Basic
AuthName "my project test"
AuthUserFile /etc/subversion/passwd
<LimitExcept GET PROPFIND OPTIONS REPORT>
Require valid-user
</LimitExcept>
</Location>

Then I test it again after restarted the apache2 using the following command:
svn co [http://server/svn/mypp](http://server/svn/mypp) --username xxx.

It didn't work and generated the following error to the screen:
svn: PROPFIND request "/svn/mypp" fail
svn: Could not open the requested SVN filesystem.

I checked the apache's error.log, the apache server output the following error messages:
[Sun Jul 02 01:28:56 2006] [error] [client 221.216.57.229] (20014)Error string not specified yet: Can't open file '/home/svn/svn/format': No such file or directory
[Sun Jul 02 01:28:56 2006] [error] [client 221.216.57.229] Could not fetch resource information.  [500, #0]
[Sun Jul 02 01:28:56 2006] [error] [client 221.216.57.229] Could not open the requested SVN filesystem  [500, #2]
[Sun Jul 02 01:28:56 2006] [error] [client 221.216.57.229] Could not open the requested SVN filesystem  [500, #2]

I couldn't find the reason:(
Any suggestions will be much appreciated.

---

