# cPanel Web Hosting: Shared, Reseller or Self-Managed VPS? What Each One Costs and the Limits That Bite After Signup (Full Plan Table)

cPanel is bundled into the price on shared hosting and billed separately on a self-managed VPS. That single line explains most of the gap between a cheap shared account and a server you rent by the hour: on DigitalOcean, Lightsail, Linode or Vultr you install cPanel yourself, use it free for 15 days, then buy a license to keep it running.

RackNerd sits firmly in the first camp. Its shared plans ship with cPanel, CloudLinux, LiteSpeed and offsite daily backups already included, and the entry reseller tier is listed at **$94 per year** for 12 separate cPanel accounts and 180 GB of NVMe storage, which works out to about $7.83 a month for the entire reseller stack.

What follows is the full plan table, a short answer on what cPanel actually does for you, the licensing math that applies the moment you leave shared hosting, and the account limits (inodes, entry processes, daily email caps) that decide whether a plan holds up once real traffic arrives.

> **Quick pick.** Running one site with one login: the 30 GB shared plan. Managing client sites that each need their own cPanel login: the reseller tier at $94/year for 12 accounts. Want root access and a stack you configure yourself: a KVM VPS, with a cPanel license bought on top.
> 👉 [See RackNerd's current cPanel hosting plans](https://bit.ly/RacKnerd)

## RackNerd's cPanel plans at a glance

All three shared tiers run the same software stack. What changes is storage, monthly transfer, and how many domains you can point at the account.

| Plan | Storage | Monthly transfer | Domains / accounts | Price | Order |
| --- | --- | --- | --- | --- | --- |
| Shared 30 GB | 30 GB NVMe | 3 TB | 2 domains | Live price at checkout | [Order the 30 GB shared plan](https://bit.ly/RacKnerd) |
| Shared 85 GB | 85 GB NVMe | 10 TB | 10 domains | Live price at checkout | [Order the 85 GB shared plan](https://bit.ly/RacKnerd) |
| Shared 200 GB | 200 GB NVMe | 30 TB | Unlimited domains | Live price at checkout | [Order the 200 GB shared plan](https://bit.ly/RacKnerd) |
| Reseller (12 accounts) | 180 GB NVMe | See order page | 12 cPanel accounts | **$94/year** | [Order the reseller plan](https://bit.ly/RacKnerd) |

RackNerd moves shared hosting pricing around with promotions and billing terms, so a hard number in a table would be wrong within a month. The order page shows the live figure for the term you select before you pay. The reseller price above is the listed annual rate.

Every RackNerd cPanel plan, shared and reseller, includes:

- cPanel with Softaculous one-click installs and the SiteJet AI site builder
- CloudLinux with KernelCare for kernel patching without reboots
- LiteSpeed web server and free SSL certificates
- Offsite daily backups through JetBackup
- Free migration from another host, provided the old host also runs cPanel
- A free Clientexec license
- MailBaby Hybrid for outbound email delivery
- A choice of US, European or Asian server locations at checkout, with activation in minutes and 24/7 support

## What cPanel actually does for you

cPanel is a web-based control panel for Linux hosting. From one dashboard you upload and edit files or connect over FTP, manage domains and DNS records, create mailboxes with IMAP, POP3 and webmail access, build MySQL databases, install or renew SSL certificates, switch PHP versions, schedule cron jobs and run backups. Login is usually `yourdomain.com/cpanel` or port 2083.

The time it saves is command-line time. It does not create CPU, RAM or I/O. On a shared plan you are still one account among many on a server, and on a VPS the panel is a management layer sitting on top of whatever resources you rented.

WHM sits one level above cPanel. It creates and isolates individual cPanel accounts, which is what makes reseller hosting possible. RackNerd's reseller tier gives you 12 of those accounts to hand out, each with its own login, its own domains and its own mailboxes.

## Where the money goes when you leave shared hosting

The license. DigitalOcean's own documentation is explicit about it: install cPanel & WHM from the Marketplace and you get a 15-day free trial, after which "you'll need to get a cPanel license in order to continue using cPanel." The server price and the license are two separate bills.

| Platform | Base server price | cPanel |
| --- | --- | --- |
| DigitalOcean | from $4/mo | Trial, then license required |
| Amazon Lightsail | from $3.50/mo | Trial, then license required |
| Linode | from $5/mo | Trial, then license required |
| Vultr | from $2.50/mo | License required |
| Google Cloud | from $8/mo | License required |

Those prices are for the server alone, before the panel. Compare that with what shared hosts do: they absorb the license into the monthly fee, which is why a $5 shared account can look cheaper than a $4 VPS once you add the panel. Bluehost packages it a third way, with cPanel included free on shared plans and free for the first year on VPS and dedicated plans.

RackNerd's standard KVM VPS line is listed from $2.24/month with full root access. cPanel is not part of that package, so if you want the panel on a VPS, budget for the license on top of the server.

Backups split into two systems once you self-manage. DigitalOcean charges 20% of the Droplet price for snapshots, which restore an entire machine. cPanel's own backups are per-account and configured inside the panel. Neither replaces the other, and on RackNerd's shared plans the offsite daily JetBackup runs are handled for you.

## The limits that show up after you pay

Sales pages list storage and bandwidth. The numbers that actually stop a site are smaller and usually buried in comparison tables or terms. The figures below come from hosting.com's published plan comparison, not from RackNerd's specifications, and they are typical of how shared cPanel accounts are metered.

**Inodes: 200,000 across every tier.** An inode is roughly one file. A brochure site with a few hundred images never notices. A WordPress store that has been running for years, with plugin-generated thumbnails, cache files and locally stored backup archives, can approach the ceiling faster than the storage graph suggests.

**Entry processes: 30, 60 or 120 depending on tier.** This is the concurrent PHP process cap. A traffic spike, or a plugin that opens several connections per page view, hits it and visitors get 503 errors while the CPU sits idle. Nothing on the pricing page tells you this number.

**Outbound email: 2,400 messages per day, 100 MB per message, 10 GB per mailbox.** Generous for contact forms and order confirmations. A newsletter send, or a compromised form script, blows through it and the account gets throttled.

**Backup retention: 30 days with self-serve restore** at hosting.com. hosted.com advertises daily backups without publishing a retention window. Retention is the number to check before you cancel your own backup routine, because "daily backups" can mean seven days or thirty.

**Page-view figures are not quotas.** The same comparison lists 50,000, 150,000 and 500,000 monthly page views, labeled as a capacity guide with no hard limits. Treat them as sizing hints.

Worth noting: that page states a 99.9% uptime SLA in the body copy and 99.95% in the comparison table. Two different numbers on one page is a good reason to read the actual service terms rather than the badge.

Add-on domains deserve their own warning. Ten domains on one cPanel account share the same CPU, RAM and entry processes. The 85 GB plan does not give you ten times the resources of the 30 GB plan, only ten times the slots. One busy site drags the rest down with it.

## Which RackNerd plan fits your situation

- **A single site, a blog, a portfolio, a small store:** the 30 GB shared plan. Two domains is enough for the site plus a staging copy or a redirect.
- **Three to ten sites you own:** the 85 GB plan. You get separate document roots and databases, but one resource pool shared across all of them.
- **Many domains, or one media-heavy site:** the 200 GB plan. Unlimited domains matters most if you park variants, run regional subdomains or host archives.
- **Client work where each customer wants their own login:** the reseller tier. Twelve cPanel accounts at $94/year, each isolated, with WHM to create and suspend them. That isolation is the reason to pay for reseller rather than piling client sites onto one shared account.
- **A custom stack, a control panel other than cPanel, or software that needs root:** a KVM VPS, with the cPanel license question answered separately.

👉 [Compare the shared and reseller plans and pick a billing term](https://bit.ly/RacKnerd)

## FAQ

**Can one cPanel account host several websites?**
Yes, through add-on domains and subdomains. Each site gets its own folder and database, and all of them draw on the same disk, memory and entry processes. That shared pool is the practical limit, not the domain count.

**Who is responsible for backups?**
On RackNerd's shared and reseller plans, offsite daily backups via JetBackup are included. On a self-managed VPS the responsibility is yours: hypervisor snapshots protect the whole machine, cPanel's own backup feature protects individual accounts, and they solve different problems. Keep an off-network copy either way.

**What happens if a cPanel license lapses?**
cPanel needs a valid license to keep operating. Losing it means losing the panel, which is where mailboxes, DNS records and SSL renewals are managed. The site files do not vanish, but routine administration becomes a command-line job.

**Is shared cPanel hosting enough for a small WooCommerce store?**
For a starter store with a handful of orders a day and a cart that is not running heavy plugins, yes, and hosted.com markets its shared tiers at exactly that use case. The constraints to watch are entry processes and memory. If you run more than one store, or expect concurrent checkouts during promotions, the reseller or VPS route removes the shared ceiling.

**Can I migrate an existing cPanel site over?**
cPanel-to-cPanel moves are the easy case: a backup and restore puts sites, mailboxes and settings back as they were. hosting.com and hosted.com both advertise free migration, and RackNerd includes free migration on any package as long as your current host also runs cPanel. Moving from a non-cPanel panel means a manual migration, so ask what that involves before you commit.

## Before you order

Three things to confirm at checkout. First, the billing term, because the per-month headline on an annual prepay is not the price you pay in year two. Second, whether cPanel is included, which it is on RackNerd's shared and reseller plans and is not on its KVM VPS line. Third, the cancellation terms, which are stricter here than on hosts advertising a blanket 30-day money-back window: prepaid account credit is not refundable, an immediate cancellation request starts a 24-hour termination countdown rather than returning your balance, and suspensions for abuse do not refund either. If you are unsure about a plan, start small and upgrade later from the client area, which RackNerd supports without a migration.

Third-party monitoring cited in independent reviews has recorded uptime averages around 99.99%, though RackNerd does not publish a formal SLA with compensation terms, so treat reliability as a track record rather than a contract.

For a single site or a handful of your own domains, the shared tiers cover it with cPanel, LiteSpeed and offsite backups in one bill. For client accounts that need separation, the 12-account reseller tier at $94/year is the cheaper route than twelve separate plans.

👉 [Start with RackNerd's cPanel hosting and choose your plan](https://bit.ly/RacKnerd)
