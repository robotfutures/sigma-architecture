> **Working draft** — comments welcome via [issues](https://github.com/robotfutures/sigma-architecture/issues); please don't cite or quote yet.

## **4. Grounding the constraints in the forces**

§3 states the model; this section grounds it. The forces of §1.4 are competing pulls, and a pattern is judged by how it resolves them. No constraint in Sigma is arbitrary as each is present at some force's demand, and each force terminates in a clause of the algebra.

### **4.1 Concurrency, volume, and pace (force 1 → constraints 3, 4, 5)**

A reasoning act is discrete against a world that moves while it runs. The TOCTOU window — check at the view out, use at the push — spans minutes to hours and is the ordinary case (§1.4.1). The cascade interrupts at one place only: the moment of entry. Basis-carried contribution, adjudicated reconciliation and explicit currency answer it.

1. Every push carries $\vec{B}$, the state it was reasoned from; with the data already resident on the substrate;
2. `push` compares $H=B$ through pointer arithmetic in $O(1)$ to guard on shifted premise.
3. The working chain's tip $T$ is classified mechanically according to policy: $t_{policy}(T) \in \{\text{ok}, \text{contested}, \text{denied}\}$
4. If ok, the chain $B..T$ is collapsed to a squash commit $c_{T}$ in $O(n)$; and
5. Finally a compare-and-swap on $U := c_{T}$, in $O(1)$

As compared to git, the merge check only asks whether *lines* collided, or the content rests on the head of the target branch. With this model, because the substrate refuses judgment (only policy), a push is tested for actor's acknowledgement of the trunk's evolution (#2, above - $H=B$) to guard against stale premises.

The refusal costs computing $\Delta(U{-}B)$ for contest, $\Delta(U{-}B) \perp T$ for conflict, and enumerating the non-conforming objects, but this is out of the critical path.

Sigma's gates are stricter than the forges, principally because context decays from the moment work is done, in humans and agents alike, so a late reckoning is (often) a worse reckoning.

### **4.2 Variable trust and reliability (force 2 → constraints 1, 2, 4)**

How do you persistently trust an agent with no persistent self? You cannot, so trust must be structural and graduated: audience-scoped truth, composed views and adjudicated reconciliation carry trust in objects — what each actor can reach, and what it can do. Dials on the different structures and gates graduate this trust for each actor.

1. _What can an actor see and touch_? is described by the mounts in the actor's workspace. These capture read/write. Changing standing is modifying the workspace definition.
2. _How does the actor's work fold into the trunks?_ is also defined at the mount. An actor with full standing can `push` to a trunk; an actor with `propose` defers the question to a trusted party that can rule.
3. _Who is trusted with reviews?_ are commits to the trunk to establish authority. These are seeded at trunk creation, via the control plane (§3.2) — and a grant can only make rules stricter than the trunk's baseline, never looser.

Every dial sits on an object the actor themselves cannot administer — $m_{policy}$ may only tighten $t_{policy}$, so no actor softens its own gate (§3.3).

Here membership is in the history — Linux keeps `MAINTAINERS` in the tree, Kubernetes keeps `OWNERS`; Sigma makes the convention obligatory (§3.2).

The gate caps what trust can waive (§3.5): a trusted writer may accept a flagged risk on the record — a disclosure — but nothing a writer says lifts a prohibition or manufactures content. The standard applied is itself auditable: $\Delta t$ sits in $H$, $B$ and timestamps.

### **4.3 Delegation (force 3 → constraints 3, 6)**

If agents are acting on our behalf, how do we distinguish a principal's judgment from their agent? Intention vs. execution can be quite different. Thus delegation splits *who answers* from *who acted*, and adds *what did they know* when they acted. (An agent's context does not survive the turn.)

Basis-carried contribution and provenance as contract address the force by taking all three at the write. Precisely, and all delivered by the substrate, not the client:

1. The workspace opens under $(principal, agent)$ (§3.2).
2. Commits seal with their author, on the chain.
3. The landing takes $(principal, agent, workspace, \vec{B})$ (§3.7).
4. The chain rides the landing as a second parent — a provenance edge — so acceptance is derivable from ancestry rather than asserted (§3.7).

The association between an agent and their principal makes transparent critical shifts in authority and authenticity.

In regulated industries, ALCOA requires a regulated record — *attributable*, *legible*, *contemporaneous*, *original*, *accurate*. These can only be provided by a substrate (§3.7) – as compared to a system like git where attribution is client-supplied.

### **4.4 Partial visibility (force 4 → constraints 1, 2)**

Privacy law and security dictate that no single actor sees everything. Audience-scoped truth and composed views answer the force by making the boundary the shape of the data itself.

The boundary is a set of structural facts:

- $\mathcal{A}$ is a component of the trunk, $t = (\mathcal{C}, \mathcal{A}, t_{policy})$ (§3.2).
- Reach is exactly $\bigcup_i s_i$ — the union of the namespace slices $s$ each mount grants (§3.2): what is not mounted does not exist for the actor.
- The mount is the capability: revocation is an unmount, attenuation is composing less, and tools arrive through the same grant — *do* and *see* are one mechanism, not two kept in agreement.
- Forks cannot widen: $\mathcal{A}' \subseteq \mathcal{A}$ (§3.8.1).

An audit follows the geometry: a privacy review reads sets — $\mathcal{A}$ per trunk, its history (who and when), and the mount table per view (how).

As compared to the forge, the boundary there is the repository — partition *or* composition. Trunks partition at the audience and recompose in the view: one workspace holds slices of many trunks, each policed by its own $\mathcal{A}$ — equivalent to Plan 9's per-process namespaces (§3.2). The same geometry settles local-first: a full replica hands the actor the repository; a served view out grants $\bigcup_i s_i$.

### **4.5 Absence of ambient context (force 5 → constraints 2, 5)**

Humans coordinate through a periphery of informal channels. An agent has none, only those engineered. The periphery has a second defect: it kept no records. Composed views and explicit currency answer both halves: the channels are trunks, and the awareness is divergence and debt, with debt acknowledgement accounted (§3.2, §3.6). While humans still maintain a periphery, the awareness channels close the gap to those not in reach.

Thus, "did the actor know about the new budget?" is a query — $H$ against the fact, per workspace. Every premise an agent holds is a premise some mount served: nameable, owned, auditable.

Side-channels (context and content flowing in and out, outside the view) outside Sigma's trunks are liabilities to the integrity of the process (having no accountability). To close this:

1. Running external facts — prices, weather, a budget — enter through a **monitor**, an actor that only writes: it deposits facts as attributed landings and never reads anything back.
2. Tools to pull information can mount through the workspace, with I/O handled like Plan 9 control files.

### **4.6 Bounded attention (force 6 → constraints 2, 5)**

Saturation degrades human judgment and model reasoning alike. Two different attention costs must be considered: what must be held in view to reason at all, and what must be re-examined when the world moves. Composed views bound the first; explicit currency bounds the second.

The cost model, per attention act:

- **Hold in view:** $O(|V|)$ for the surface $V_B$ (§3.2). Fine-grained trunks, and finer-grained mounts narrow the accessible space within $V_B$.
- **Am I current:** $O(1)$ per trunk — the comparison $H = B$, however large the world has grown (§3.3).
- **Catch up:** $O(|\Delta|)$ — the windows $H..B$ and $B..U$ served as deltas, costing the net change.
- **Discharge:** per trunk, on the actor's schedule, qualified where understanding is partial (§3.4, §3.6) — on the actor's consumption schedule.

Every attention cost is bounded by something the deployment chooses — $|V|$, the net delta — and none by the size of the world or the rate at which it produces events. In this regard, Sigma presents like an event-sourcing model, with changes collapsed in $V$ to the final state. If the actor needs the evolution, this is available looking at history over $H..B$, first with metadata, then per object.

### **4.7 Quadratic awareness (force 7 → constraints 1, 5)**

$W$ collaborators attending to one another is $W(W-1)/2$ pairwise relationships (Brooks, 1975). §1.4 leaves two questions open: whether the cost is measurable, and whether the topology partitions it. Explicit currency answers the first; audience-scoped truth answers the second.

Attention attaches to objects, never to peers, and the dimension swap does the work:

- An actor's awareness state is $\{\beta_t\}_{t \in V}$ — one $(B, H)$ per mounted trunk — so its cost is dimensioned by $|V|$, never by $W$ (§3.3).
- A collaborator joining a trunk the actor does not mount costs it nothing.
- Fan-in collapses: whatever lands on a mounted trunk arrives as one delta, regardless of how many writers produced it.
- Contention is per trunk, bounded by $|\mathcal{A}|$ at creation; the CAS serializes a trunk, never the collaboration (§3.2).
- The topology partitions the remainder: a fork reconciles once per boundary, its $M$ workspaces catch up locally, and debt travels one boundary at a time (§3.8.2).

This cost is absorbed by the ledger, per $(w, t)$. It reads who is behind, on what, since when. Keeping $W$ small on a trunk is an operation on the topology — split a trunk, add a tier (§6.4.2). The quadratic is not resolved away; Sigma can only offer mechanisms to linearize it.

### **4.8 Stemming the failure cascade**

The responses to the forces look fine and good, but: _does Sigma stem the domain's failure cascade (§1.4.1)_?

No.

Nothing can – beyond the collaborators themselves by actively exercising the capacities named in §1.2. What Sigma does is close the gap between those activities and the work, especially for agents. A Sigma deployment:

- Encodes structural rules of engagement through audiences, views, and landing authority;
- Forces timely reckoning by gating suspect work;
- Delivers mutual awareness as debt and divergence; and,
- Records attributed judgment for transparency and authenticity.

All of these in support of the continuous recomposing and grounding of the work, by the collaborators through their rendered judgment. Making these activities low cost to effortless and coordinated through a single substrate is what aligns and maintains a coherent body of work.
