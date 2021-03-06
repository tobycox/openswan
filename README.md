openswan Cookbook
=================
Install and configure openswan for per-user l2tp over ipsec vpn access.

Requirements
------------
Currently tested only on Ubuntu 12, and expects a 'users' databag, with user records formatted like this:

    {
        "groups":["sysadmin", "vpn"],
        "comment":"Jane Doe",
        "username":"jane",
        "id":"jane",
        ...
        "vpn_password":"someverysecurepassword"
    }


Attributes
----------
Default attributes should be overwritten to match your role or environment needs.

    default['openswan']['ppp_link_network'] = "10.55.55.0"
    default['openswan']['preshared_key'] = "letmein"
    default['openswan']['private_virtual_interface_ip'] = "10.55.55.4"
    default['openswan']['private_ip'] = `ifconfig eth1 | grep "inet addr" | awk 'BEGIN{FS=":"}{print $2}' | awk '{print $1}'`.strip
    default['openswan']['private_ip_range'] = "10.55.55.5-10.55.55.100"
    default['openswan']['xl2tpd_path'] = "/etc/xl2tpd"
    default['openswan']['ppp_path'] = "/etc/ppp"


License and Authors
-------------------
Author: Blake Irvin (bixu@wanelo.com)

Based on original work by Ryan Nelson (ryan.nelson@joyent.com), with input from Eric Saxby (sax@wanelo.com) and Konstanin Gredeskoul (kig@wanelo.com)
