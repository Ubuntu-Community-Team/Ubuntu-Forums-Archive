---
title: "Self signed sertificate stopped working autum 2024 with error remote error: tls: unkn"
date: 2024-09-10
forum: General Help
---

### Post by sigmano on 2024-09-10
I am generating a self signed certificate in Ubuntu. 


The certificates generated are:

* /etc/ssl/certs/rootCA_$my_ip.nopass.pem+key.pem
* /etc/ssl/certs/rootCA_$my_ip.crt
* /etc/ssl/certs/server_$my_ip.nopass.key
* /etc/ssl/certs/server_$my_ip.pem
* /etc/ssl/certs/server_$my_ip.crt


I am trying to use them in a LimaCharlie Adapter but I get the following error:

conn.Read(): remote error: tls: unknown certificate authority

What am I doing wrong? It worked this summer..

[B]opt/certs/password.txt
[/B]I have a password file with a random password that I use also.


```
ae8ohM1eis7Ubo
```



**rootCA_openssl.cnf**
Next I have generated a rootCA_openssl.cnf file.

```
[ req ]
distinguished_name = req_distinguished_name
req_extensions = v3_req
prompt = no
 
[ req_distinguished_name ]
countryName = NO
stateOrProvinceName = Oslo
organizationName = Gorgon Shipping
commonName = Gorgon Shipping Root CA 34.88.113.95
 
[ v3_req ]
basicConstraints = CA:true
keyUsage = critical, keyCertSign
```

**server_openssl.cnf**
I have a server openssl file to generate a server certificate.

```
[ req ]
distinguished_name = req_distinguished_name
req_extensions = v3_req
prompt = no

[ req_distinguished_name ]
countryName = NO
stateOrProvinceName = Oslo
localityName = Oslo
organizationName = Gorgon Shipping
commonName = 34.88.113.95
 
[ v3_req ]
basicConstraints = CA:FALSE
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
subjectAltName = @alt_names
 
[ alt_names ]
IP.1 = 34.88.113.95
```


[B]opt/certs/generate_certificates.sh
[/B]Now I have a script that uses the files above to generate two certificates. 

```
#!/bin/bash

# Variables
echo "VARIABLES"
my_ip=$(curl -s ifconfig.me)
certificate_password=$(cat /opt/certs/password.txt)
date_ymd=$(date +"%Y-%m-%d")
customer_abbreviation=dev
hostname=$(hostname)
os_id=$(lsb_release -is)
os_version=$(lsb_release -sr)


# CD
cd /opt/certs

# Root CA
echo "ROOT CA"
openssl genrsa -aes256 -out rootCA_$my_ip.key --passout pass:$certificate_password 2048
openssl req -new -key rootCA_$my_ip.key -out rootCA_$my_ip.csr -config rootCA_openssl.cnf --passin pass:$certificate_password
openssl x509 -req -in rootCA_$my_ip.csr -sha512 -signkey rootCA_$my_ip.key -out rootCA_$my_ip.pem -days 1095 -extensions v3_req -extfile rootCA_openssl.cnf --passin pass:$certificate_password

openssl rsa -in rootCA_$my_ip.key -out rootCA_$my_ip.nopass.key --passin pass:$certificate_password


# Convert the PEM files to CRT
openssl x509 -in rootCA_$my_ip.pem -out rootCA_$my_ip.crt

# Root CA :: Combine the no-password private key and the certificate into one file
cat rootCA_$my_ip.nopass.key rootCA_$my_ip.pem > rootCA_$my_ip.nopass.pem+key.pem

# Root CA :: Combine the password private key and the certificate into one file
cat rootCA_$my_ip.key rootCA_$my_ip.pem > rootCA_$my_ip.pem+key.pem

# Server CA
echo "SERVER CA"
openssl genrsa -aes256 -out server_$my_ip.key --passout pass:$certificate_password 2048
openssl req -new -key server_$my_ip.key -out server_$my_ip.csr -config server_openssl.cnf --passin pass:$certificate_password
openssl x509 -req -in server_$my_ip.csr -sha256 -CA rootCA_$my_ip.pem -CAkey rootCA_$my_ip.key -out server_$my_ip.pem -days 1095 -extensions v3_req -extfile server_openssl.cnf --passin pass:$certificate_password

openssl rsa -in server_$my_ip.key -out server_$my_ip.nopass.key --passin pass:$certificate_password

# Convert the PEM files to CRT
openssl x509 -in server_$my_ip.pem -out server_$my_ip.crt

# Verify
echo "VERIFY"
openssl verify -verbose -CAfile rootCA_$my_ip.pem server_$my_ip.pem


# Copy certificates to /etc/ssl/certs/ so we can use them with rsyslog
cp rootCA_$my_ip.nopass.pem+key.pem /etc/ssl/certs/rootCA_$my_ip.nopass.pem+key.pem
cp rootCA_$my_ip.crt /etc/ssl/certs/rootCA_$my_ip.crt

cp server_$my_ip.nopass.key /etc/ssl/certs/server_$my_ip.nopass.key
cp server_$my_ip.pem /etc/ssl/certs/server_$my_ip.pem
cp server_$my_ip.crt /etc/ssl/certs/server_$my_ip.crt

chmod 644 rootCA_$my_ip.nopass.pem+key.pem /etc/ssl/certs/rootCA_$my_ip.nopass.pem+key.pem
chmod 644 rootCA_$my_ip.crt /etc/ssl/certs/rootCA_$my_ip.crt

chmod 644 server_$my_ip.nopass.key /etc/ssl/certs/server_$my_ip.nopass.key
chmod 644 server_$my_ip.pem /etc/ssl/certs/server_$my_ip.pem
chmod 644 server_$my_ip.crt /etc/ssl/certs/server_$my_ip.crt


# Update Certificate store
sudo update-ca-certificates
```

---

### Post by ActionParsnip on 2024-09-10
If you access the service using a web browser (I assume its a web server), do you see the certificate? Who is the issuer?

---

