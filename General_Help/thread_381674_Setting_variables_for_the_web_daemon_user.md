---
title: "Setting variables for the web daemon user"
date: 2007-03-11
forum: General Help
---

### Post by buFka on 2007-03-11
i want to connect oracle via php, but i get this error message:
> Warning: ocilogon() [function.ocilogon]: OCIEnvNlsCreate() failed. There is something wrong with your system - please check that ORACLE_HOME is set and points to the right directory in /var/www/powl-mysql/test_oracle.php on line 2

so i think, oracle_home is not set correctly, i have found some info [here]("http://de2.php.net/oci8"):

>  Before using this extension, make sure that you have set up your Oracle environment variables properly for the Oracle user, as well as your web daemon user. These variables should be set up before you start your web-server. The variables you might need to set are as follows:

    * ORACLE_HOME
    * ORACLE_SID
    * LD_PRELOAD
    * LD_LIBRARY_PATH
    * NLS_LANG 

so...how can i set this variables for the web daemon user?

---

