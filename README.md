# ♻️ NovaRecycle

> **The Operating System for Resource Recovery.**
> Digital management of Material Recovery Facilities (MRF), urban mining, and automated sorting centers.

[](https://www.google.com/search?q=https://github.com/novaeco-tech/novarecycle/actions)
[](https://opensource.org/licenses/MIT)
[](https://www.google.com/search?q=https://recycling.novaeco.tech)

**NovaRecycle** is the Vertical Sector responsible for the **End-of-Life** (and **Re-Birth**) phase of the circular economy. While `NovaLogistics` handles the *movement* of waste, **NovaRecycle** handles the *processing*. It runs the software inside sorting centers, scrap yards, and chemical recycling plants.

It transforms mixed, low-value waste streams into high-value "Secondary Raw Materials" (SRM) ready for `NovaTrade`.

-----

## 🎯 Value Proposition

The goal is to turn the city into a mine ("Urban Mining"). **NovaRecycle** provides the digital infrastructure to:

1.  **Automate Sorting:** Orchestrate robotic arms and air-jets (via `NovaInfra`) to separate materials based on `NovaMind` vision data.
2.  **Verify Recovery:** Prove to regulators that 10 tons of plastic were actually recycled, not incinerated (Compliance with **EU Waste Shipment Regulation**).
3.  **Material Valuation:** Real-time calculation of the "Ore Grade" of incoming waste (e.g., "This truckload of e-waste contains €5,000 of Gold").

-----

## 🏗️ Architecture (The Transformation Factory)

NovaRecycle acts as a Manufacturing Execution System (MES) for trash. It tracks mass flow balance (Input = Output + Loss).

```mermaid
graph TD
    User((Facility Manager)) -->|HTTPS| UI[NovaRecycle Dashboard]
    UI -->|REST| API[NovaRecycle API]
    
    subgraph "The Input (Gate)"
        API -->|Weight/Scan| Infra[NovaInfra (Weighbridge)]
        API -->|Validate Carrier| Logistics[NovaLogistics]
    end

    subgraph "The Sorting Line"
        Infra -->|Camera Stream| Mind[NovaMind]
        Mind -->|Material ID| API
        API -->|Sort Command| Infra[Robotic Sorters]
    end

    subgraph "The Output (Bales)"
        API -->|Mint Material Batch| Mat[NovaMaterial]
        API -->|List for Sale| Trade[NovaTrade]
        API -->|Mass Balance Audit| Balance[NovaBalance]
    end
```

### Integrated Services

  * **[NovaInfra](https://www.google.com/search?q=https://infrastructure.novaeco.tech):** Controls the industrial hardware—conveyor belts, weighbridges, NIR (Near-Infrared) scanners, and balers.
  * **[NovaMind](https://www.google.com/search?q=https://mind.novaeco.tech):** The eyes. Distinguishes between PET (Water bottles) and HDPE (Shampoo bottles) milliseconds before they hit the sorter.
  * **[NovaMaterial](https://www.google.com/search?q=https://materials.novaeco.tech):** The birth certificate. When recycling finishes, NovaRecycle creates a *new* Passport for the "Recycled Pellet Batch."
  * **[NovaTrade](https://www.google.com/search?q=https://trade.novaeco.tech):** The sales channel. Automatically lists produced bales (e.g., "1 Ton Grade A Aluminum") on the wholesale market.

-----

## ✨ Key Features

### 1\. Smart Sorting Logic

Configurable routing logic for the facility.

  * **Dynamic Recipes:** Switch the sorting line mode based on market prices from `NovaTrade`.
      * *Scenario:* "Price of Clear PET is up. Switch optical sorters to prioritize Clear over Colored."

### 2\. Mass Balance Accounting

The anti-fraud engine.

  * **Input:** 100 Tons of Mixed Trash.
  * **Output:** 60 Tons Metal, 20 Tons Plastic, 20 Tons Residue.
  * **Audit:** If a facility claims to produce 110 Tons of output from 100 Tons of input, `NovaBalance` flags a "Phantom Inventory" fraud alert.

### 3\. Digital Waste Transfer Notes (dWTN)

Automated compliance.

  * Generates the legal manifest required to move hazardous waste (e.g., batteries from `NovaTronix`).
  * Cryptographically signs the handover from Hauler -\> Recycler.

### 4\. Urban Mining Yields

Predictive analytics for city planners.

  * Integrates with `product-urban-miner` to report: "We recovered 40kg of Rare Earth Elements this month."

-----

## 🚀 Getting Started

We use **DevContainers** to provide a consistent development environment.

### Prerequisites

  * Docker Desktop
  * VS Code (with Remote Containers extension)

### Installation

1.  **Clone the repo:**
    ```bash
    git clone https://github.com/novaeco-tech/novarecycle.git
    cd novarecycle
    ```
2.  **Open in VS Code:**
      * Run `code .`
      * Click **"Reopen in Container"** when prompted.
3.  **Start the Sector:**
    ```bash
    make dev
    ```
      * **Dashboard:** http://localhost:3000 (Facility Control Panel)
      * **API:** http://localhost:8000/docs

### Configuration (`.env`)

```ini
# Facility Settings
FACILITY_TYPE=MRF # or E_WASTE, CHEMICAL, COMPOST
SORTING_CAPACITY_TPH=50 # Tons Per Hour

# Integrations
NOVAINFRA_URL=http://novainfra-api:8000
NOVAMIND_URL=http://novamind-api:50051
```

-----

## 📂 Repository Structure

This is a Monorepo containing the sector's specific logic.

```text
novarecycle/
├── api/                # Python/FastAPI (The Factory Brain)
│   ├── src/
│   │   ├── inbound/    # Weighbridge & dWTN logic
│   │   ├── sorting/    # Algorithm to route materials to bins
│   │   └── outbound/   # Bale generation & NovaTrade listing
├── app/                # React/Next.js Frontend (Operator UI)
│   ├── src/
│   │   ├── live-view/  # Real-time conveyor visualization
│   │   └── reports/    # Yield & Mass Balance charts
├── website/            # Documentation (Docusaurus)
└── tests/              # Integration tests
```

-----

## 🧪 Testing

We use **Process Simulation** for testing.

  * **Mass Balance:** `make test-balance`
      * Simulates a 24h shift. Asserts that `Input Mass == Output Mass + Loss`.
  * **Contamination Test:** `make test-purity`
      * Simulates a "Lithium Battery" entering a "Paper Line." Verifies that the system triggers an emergency stop event via `NovaInfra`.

-----

## 🤝 Contributing

We need contributors with backgrounds in **Industrial Automation**, **Waste Management**, and **Process Engineering**.
See [CONTRIBUTING.md](https://www.google.com/search?q=../.github/CONTRIBUTING.md) for details.

**Maintainers:** `@novaeco-tech/maintainers-sector-novarecycle`