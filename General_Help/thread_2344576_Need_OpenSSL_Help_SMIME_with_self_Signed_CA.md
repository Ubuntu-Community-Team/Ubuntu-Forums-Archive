---
title: "Need OpenSSL Help S/MIME with self Signed CA"
date: 2016-11-26
forum: General Help
---

### Post by RadarG on 2016-11-26
A few years ago I created a self signed CA cert and x509 s/mime cert and I was able to import my newly created CA and X509 certs into two IOS devices. I was able to sign digitally sign and encrypt emails. My CA has since expired and I need to create another one however I forgot how I did it. I can import the CA and the s/mime X590 certs into my ipad however it will not let me encrypt the emails. Here is the commands that I used to create the CA and x509 certs. Can someone tell me what I'm doing wrong? I am using a ipad air 2 running IOS 10.1.1

    openssl req -x509 -config openssl-ca.cnf -newkey rsa:4096 -days 4000 -sha512 -nodes -out cacert.pem -outform PEM

    openssl req -config openssl-server.cnf -newkey rsa:4096 -sha512 -nodes -out servercert.csr -outform PEM echo '01' > serial.txt

    openssl ca -config openssl-ca.cnf -policy signing_policy -extensions signing_req -out servercert.pem -infiles servercert.csr

    openssl pkcs12 -export -in cacert.pem -inkey cakey.pem -out CA.p12 -name "mykey" openssl pkcs12 -export -in servercert.pem -inkey serverkey.pem -out email4.p12 -name "email"
 
here is the config files

CA file

HOME            = .

RANDFILE        = $ENV::HOME/.rnd

####################################################################

[ ca ]
default_ca  = CA_default        # The default ca section
[ CA_default ]
default_days = 1825          # how long to certify for
default_crl_days= 1820            # how long before next CRL
default_md  = sha512        # use public key default MD
preserve    = no            # keep passed DN ordering
x509_extensions = ca_extensions     # The extensions to add to the cert
email_in_dn = no            # Don't concat the email in the DN
copy_extensions = copy          # Required to copy SANs from CSR to cert
base_dir    = .
certificate = $base_dir/cacert.pem  # The CA certifcate
private_key = $base_dir/cakey.pem   # The CA private key
new_certs_dir   = $base_dir     # Location for new certs after signing
database    = $base_dir/index.txt   # Database index file
serial      = $base_dir/serial.txt  # The current serial number
unique_subject  = no            # Set to 'no' to allow creation of

                # several certificates with same subject.
####################################################################
[ req ]
default_bits        = 4096
default_keyfile     = cakey.pem
distinguished_name  = ca_distinguished_name
x509_extensions     = ca_extensions
string_mask         = utf8only
####################################################################
[ ca_distinguished_name ]
countryName         = Country Name (2 letter code)
countryName_default     = XX
stateOrProvinceName     = State or Province Name (full name)
stateOrProvinceName_default = XX
localityName            = Locality Name (eg, city)
localityName_default        = XX
organizationName            = Organization Name (eg, company)
organizationName_default    = Test CA, Limited
organizationalUnitName  = Organizational Unit (eg, division)
organizationalUnitName_default  = Server Research Department
commonName          = Common Name (e.g. server FQDN or YOUR name)
commonName_default      = CA-01
emailAddress            = Email Address
emailAddress_default        = XXXXX@XXXXX
####################################################################
[ ca_extensions ]
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid:always, issuer
basicConstraints = critical, CA:true
keyUsage = keyCertSign, cRLSign
####################################################################
[ signing_policy ]
countryName     = optional
stateOrProvinceName = optional
localityName        = optional
organizationName    = optional
organizationalUnitName  = optional
commonName      = supplied
emailAddress        = optional
####################################################################
[ signing_req ]
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid,issuer
Server file
\HOME            = .
RANDFILE        = $ENV::HOME/.rnd
####################################################################
[ req ]
default_bits        = 4096
default_keyfile     = serverkey.pem
distinguished_name  = server_distinguished_name
req_extensions      = server_req_extensions
string_mask         = utf8only
####################################################################
[ server_distinguished_name ]
countryName         = Country Name (2 letter code)
countryName_default     = XX
stateOrProvinceName     = State or Province Name (full name)
stateOrProvinceName_default = XX
localityName            = Locality Name (eg, city)
localityName_default        = XX
organizationName            = Organization Name (eg, company)
organizationName_default    = XX
commonName          = Common Name (e.g. server FQDN or YOUR name)
commonName_default      = [email]example@example.com[/email]
emailAddress            = Email Address
emailAddress_default        = [email]example@example.com[/email]
####################################################################
[ server_req_extensions ]
subjectKeyIdentifier        = hash
basicConstraints        = CA:FALSE
keyUsage            = digitalSignature, keyEncipherment
subjectAltName          = @alternate_names
nsComment           = "OpenSSL Generated Certificate"
####################################################################
[ alternate_names ]
DNS.1       = example.com
DNS.2       = [www.example.com](www.example.com)
DNS.3       = mail.example.com
DNS.4       = ftp.example.com

---

