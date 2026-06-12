---
title: "OpenCA authentication with LDAP server"
date: 2013-06-08
forum: General Help
---

### Post by invader7 on 2013-06-08
Hello , i have an openca installation up and running and now i want to generate certificate requests througth the "Authenticated Browser Certificate Request" form.

It requires a valid ldap connection in order to bind user fields for the certificate.

I have configured LDAP Admin and connected to my ldap server in order to verify its working. 

Now in openca i changed the settings in datasources.xml but i cant login.

My settings :

```
<datasources>
   <item>
      <name>the name of source</name>
      <type>ldap</type>
      <loa>Medium</loa>
      <address>example.com</address>
      <port>389</port>
      <attributes>
         <item>
            <name>basedn</name>
            <value>dc=example,dc=com</value>
         </item>
         <item>
            <name>loginattribute</name>
            <value>uid</value>
         </item>
         <item>
            <name>protocol</name>
            <value>ldap</value>
         </item>
         <item>
            <name>sslversion</name>
            <value>tlsv1</value>
         </item>
         <item>
            <name>sslverify</name>
            <value>none</value>
         </item>
         <item>
            <name>sslciphers</name>
            <value />
         </item>
         <item>
            <name>sslcapath</name>
            <value />
         </item>
         <item>
            <name>sslcafile</name>
            <value />
         </item>
      </attributes>
      <map>
         <entry>
            <name>dndUid</name>
            <value>userIdentifier</value>
         </entry>
      </map>
   </item>
</datasources>
```


SOLVED !! 

{OpenCA DIR}/lib/openca/functions/datasource-utils.lib 

at function dsLdapConnect added 
```

if ( $protocol == "ldap") {
    $ldap = Net::LDAP->new($ds->{address},port => $ds->{port});
    return $ldap;
}

```

---

