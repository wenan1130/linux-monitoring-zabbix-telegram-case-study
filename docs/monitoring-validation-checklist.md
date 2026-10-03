# Infrastructure Monitoring Validation Checklist

This checklist validates a Zabbix-based monitoring environment covering Linux servers, network devices, SNMP monitoring, alerting, and Telegram notifications.

---

## 1. Zabbix Server Validation

- [ ] Zabbix Server service is running
- [ ] Zabbix frontend is accessible
- [ ] Database connection is healthy
- [ ] Required hosts are visible
- [ ] Latest data is updating
- [ ] No critical internal Zabbix errors are present

---

## 2. Linux Server Monitoring

- [ ] Zabbix Agent is installed
- [ ] Zabbix Agent service is running
- [ ] Host is reachable from Zabbix Server
- [ ] CPU metrics are collected
- [ ] Memory metrics are collected
- [ ] Load metrics are collected
- [ ] Uptime is collected
- [ ] Filesystem utilization is collected
- [ ] Required processes are monitored
- [ ] Required services are monitored

Typical checks may include:

```bash
systemctl status zabbix-agent
systemctl --failed

3. Network Device Monitoring
For switches, routers, firewalls, UPS devices, and other SNMP-capable infrastructure:
- [ ] Device is reachable
- [ ] SNMP is enabled
- [ ] SNMP credentials are configured securely
- [ ] Zabbix can poll the device
- [ ] Device uptime is collected
- [ ] Interface status is collected
- [ ] Interface traffic is collected
- [ ] Interface errors are collected
- [ ] CPU utilization is collected where supported
- [ ] Memory utilization is collected where supported
- [ ] Temperature is collected where supported
- [ ] Fan status is collected where supported
- [ ] Power supply status is collected where supported
SNMPv3 is preferred where supported.
4. Interface Monitoring
- [ ] Interface operational status is visible
- [ ] Traffic utilization is visible
- [ ] Inbound traffic is collected
- [ ] Outbound traffic is collected
- [ ] Error counters are collected
- [ ] Discard counters are collected
- [ ] Important uplinks are identified
- [ ] Unused interfaces do not generate unnecessary alerts
5. Trigger Validation
- [ ] Host unavailable trigger works
- [ ] High CPU trigger works
- [ ] High memory trigger works
- [ ] Low disk space trigger works
- [ ] Service failure trigger works
- [ ] Network device unavailable trigger works
- [ ] Interface down trigger works where appropriate
- [ ] Trigger severity is appropriate
- [ ] Trigger recovery works correctly
6. Telegram Alert Validation
- [ ] Telegram integration is configured
- [ ] Test notification is delivered
- [ ] Problem notification is delivered
- [ ] Recovery notification is delivered
- [ ] Message contains hostname or device name
- [ ] Message contains problem description
- [ ] Message contains severity
- [ ] Message contains event time
- [ ] Message contains enough context for response
Do not publish Telegram bot tokens or production chat identifiers.
7. Alert Noise Review
- [ ] Duplicate alerts are minimized
- [ ] Non-actionable alerts are disabled or tuned
- [ ] Maintenance windows are configured where needed
- [ ] Flapping conditions are controlled
- [ ] Recovery notifications are enabled where useful
- [ ] Severity reflects business impact
- [ ] Alerts are understandable without opening multiple dashboards
8. Dashboard Validation
- [ ] Critical hosts are visible
- [ ] Linux server health is visible
- [ ] Network device health is visible
- [ ] Current problems are visible
- [ ] Storage status is visible
- [ ] Important interfaces are visible
- [ ] Historical trends are available
- [ ] Dashboard can be understood quickly during an incident
9. Operational Job Monitoring
Where applicable:
- [ ] Backup status is monitored
- [ ] Scheduled job status is monitored
- [ ] Data update status is monitored
- [ ] Application health checks are monitored
- [ ] Failed jobs generate alerts
- [ ] Recovery or successful rerun is visible
10. Security Validation
- [ ] Production credentials are not exposed
- [ ] SNMPv3 is used where supported
- [ ] SNMP community strings are protected
- [ ] Telegram bot token is protected
- [ ] Zabbix credentials are protected
- [ ] Access permissions follow least privilege
- [ ] Public documentation is sanitized
11. Final Acceptance Gate
Monitoring should only be considered ready when:
- [ ] Linux server monitoring passes
- [ ] Network device monitoring passes
- [ ] SNMP polling passes
- [ ] Required triggers work
- [ ] Telegram notification works
- [ ] Recovery notification works
- [ ] Dashboard displays expected status
- [ ] Alert noise is acceptable
- [ ] No unresolved critical monitoring gap remains
Monitoring Validation Result:

[ ] PASS
[ ] PASS WITH OBSERVATIONS
[ ] FAIL

Validated by:
Date:
Environment:
Open issues:

12. Validation Result


uptime
free -m
df -h
