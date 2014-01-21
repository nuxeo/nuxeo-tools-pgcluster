## About

This script can be used to automatically setup a PostgreSQL master and replica.  
It will set up streaming replication as well as WAL shipping through Amazon S3 with Wal-E (which also provides a convenient way to backup and restore).

## Warnings

This script should **not** be run on an existing installation, it does not try to preserve any existing settings or data.

Replication and failover are not trivial subjects, you should not deploy this kind of setup in production without understanding how things work.  
PostgreSQL has great documentation, feel free to peruse it!

## Requirements

The target environment (the VMs where the master and replica will be deployed) is Ubuntu. It probably also runs on Debian with very little tweaking.

This script requires `ansible 1.3.3` to run.

install with:

    pip install ansible==1.3.3

NB : if you don't have pip, it's in the python-pip package on Ubuntu, can also be installed with easy_install pip

## Configuration

In the `hosts-test` file, replace the IP addresses with those of your desired master and replica VMs.  
In the `group_vars/test` file, set up your desired PostgreSQL and S3 settings.

If you want to work with multiple environments, you can use other hosts files that will use another group with its own variables.  
For instance, copy `hosts-test` to `hosts-qa`, replace *test* with *qa* in that file, and put the associated settings in   `group_vars/qa`.

## Usage

    pgsetup <hosts-file>


