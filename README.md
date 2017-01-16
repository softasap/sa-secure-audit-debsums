sa-secure-audit-debsums
=======================
[![Build Status](https://travis-ci.org/softasap/sa-secure-audit-debsums.svg?branch=master)](https://travis-ci.org/softasap/sa-secure-audit-debsums)


Example of use: check box-example

Simple:

```YAML


     - {
         role: "sa-secure-audit-debsums"
       }

```


Advanced:

```YAML


     - {
         role: "sa-secure-audit-debsums"
       }


```


Verify every installed package including configuration files.

```bash

sudo debsums -a

```


Verify installed packages and report only errors

```bash

sudo debsums -s

```

Verify every installed package and report only changed files.

```bash

sudo debsums -c

```


Verify every installed package including configuration files and report only changed files.

```bash

sudo debsums -ca

```


Verify every installed package and report only changed configuration files.

```bash

sudo debsums -ce

```


Verify specific package and its configuration files.

```bash

sudo debsums -a bash	

```


Get a list of packages with missing or modified file.

```bash

dpkg-query -S $(sudo debsums -c 2>&1 | sed -e "s/.*file \(.*\) (.*/\1/g") | cut -d: -f1 | sort -u

```


Use generated list to reinstall group of packages.
```bash

sudo apt-get install --reinstall $(dpkg-query -S $(sudo debsums -c 2>&1 | sed -e "s/.*file \(.*\) (.*/\1/g") | cut -d: -f1 | sort -u)

```





Copyright and license
---------------------

Code licensed under the [BSD 3 clause] (https://opensource.org/licenses/BSD-3-Clause) or the [MIT License] (http://opensource.org/licenses/MIT).

Subscribe for roles updates at [FB] (https://www.facebook.com/SoftAsap/)
