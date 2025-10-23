# dapinku
app dapin
<!DOCTYPE html>
<html lang="id">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>AmanahKu - Manajemen Pinjaman Pribadi</title>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css" rel="stylesheet" />
    <style>
      * {
        margin: 0;
        padding: 0;
        box-sizing: border-box;
      }

      :root {
        --primary-rose: #ff9a9e;
        --secondary-rose: #fecfef;
        --accent-gold: #ffd700;
        --accent-pink: #fbc2eb;
        --light-pink: #fff5f7;
        --white: #ffffff;
        --text-dark: #4a4a4a;
        --text-light: #7a7a7a;
        --success: #56ab2f;
        --warning: #f7b731;
        --danger: #eb3b5a;
        --shadow: 0 10px 30px rgba(255, 154, 158, 0.2);
        --shadow-hover: 0 15px 40px rgba(255, 154, 158, 0.3);
      }

      body {
        font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
        background: linear-gradient(-45deg, #ff9a9e, #fecfef, #fbc2eb, #a6c1ee, #ffd1dc);
        background-size: 400% 400%;
        animation: gradientFlow 15s ease infinite;
        min-height: 100vh;
        color: var(--text-dark);
      }

      @keyframes gradientFlow {
        0% {
          background-position: 0% 50%;
        }
        50% {
          background-position: 100% 50%;
        }
        100% {
          background-position: 0% 50%;
        }
      }

      .container {
        max-width: 1400px;
        margin: 0 auto;
        padding: 20px;
      }

      header {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(15px);
        border-radius: 25px;
        padding: 30px;
        margin-bottom: 30px;
        box-shadow: var(--shadow);
        animation: slideDown 0.8s ease;
      }

      @keyframes slideDown {
        from {
          opacity: 0;
          transform: translateY(-30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      .header-content {
        display: flex;
        justify-content: space-between;
        align-items: center;
        flex-wrap: wrap;
        gap: 20px;
      }

      .logo {
        display: flex;
        align-items: center;
        gap: 15px;
      }

      .logo i {
        font-size: 2.5rem;
        background: linear-gradient(135deg, var(--primary-rose), var(--accent-pink));
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        animation: pulse 2s infinite;
      }

      @keyframes pulse {
        0%,
        100% {
          transform: scale(1);
        }
        50% {
          transform: scale(1.1);
        }
      }

      h1 {
        font-size: 2.2rem;
        background: linear-gradient(135deg, var(--primary-rose), var(--accent-pink));
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }

      .date-time {
        font-size: 1rem;
        color: var(--text-light);
        text-align: right;
      }

      .dashboard {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
        gap: 20px;
        margin-bottom: 30px;
        animation: fadeIn 1s ease;
      }

      @keyframes fadeIn {
        from {
          opacity: 0;
        }
        to {
          opacity: 1;
        }
      }

      .stat-card {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        border-radius: 20px;
        padding: 25px;
        box-shadow: var(--shadow);
        transition: all 0.3s ease;
        position: relative;
        overflow: hidden;
      }

      .stat-card::before {
        content: "";
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        height: 4px;
        background: linear-gradient(90deg, var(--primary-rose), var(--accent-pink));
      }

      .stat-card:hover {
        transform: translateY(-8px) scale(1.02);
        box-shadow: var(--shadow-hover);
      }

      .stat-icon {
        width: 60px;
        height: 60px;
        border-radius: 15px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.8rem;
        margin-bottom: 15px;
        background: linear-gradient(135deg, var(--primary-rose), var(--accent-pink));
        color: white;
        animation: float 3s ease-in-out infinite;
      }

      @keyframes float {
        0%,
        100% {
          transform: translateY(0);
        }
        50% {
          transform: translateY(-10px);
        }
      }

      .stat-value {
        font-size: 2rem;
        font-weight: bold;
        color: var(--text-dark);
        margin-bottom: 5px;
      }

      .stat-label {
        color: var(--text-light);
        font-size: 0.95rem;
      }

      .main-content {
        display: grid;
        grid-template-columns: 1fr 2fr;
        gap: 25px;
      }

      .card {
        background: rgba(255, 255, 255, 0.95);
        backdrop-filter: blur(10px);
        border-radius: 25px;
        padding: 30px;
        box-shadow: var(--shadow);
        animation: slideUp 0.8s ease;
      }

      @keyframes slideUp {
        from {
          opacity: 0;
          transform: translateY(30px);
        }
        to {
          opacity: 1;
          transform: translateY(0);
        }
      }

      .card-title {
        font-size: 1.5rem;
        margin-bottom: 25px;
        color: var(--text-dark);
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .card-title i {
        color: var(--primary-rose);
      }

      .form-group {
        margin-bottom: 20px;
      }

      label {
        display: block;
        margin-bottom: 8px;
        font-weight: 600;
        color: var(--text-dark);
      }

      input,
      select,
      textarea {
        width: 100%;
        padding: 12px 15px;
        border: 2px solid var(--light-pink);
        border-radius: 12px;
        font-size: 1rem;
        transition: all 0.3s ease;
        background: var(--white);
      }

      input:focus,
      select:focus,
      textarea:focus {
        outline: none;
        border-color: var(--primary-rose);
        box-shadow: 0 0 0 3px rgba(255, 154, 158, 0.2);
      }

      .input-group {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 15px;
      }

      .btn {
        padding: 12px 25px;
        border: none;
        border-radius: 12px;
        font-size: 1rem;
        font-weight: 600;
        cursor: pointer;
        transition: all 0.3s ease;
        display: inline-flex;
        align-items: center;
        gap: 8px;
      }

      .btn-primary {
        background: linear-gradient(135deg, var(--primary-rose), var(--accent-pink));
        color: white;
        width: 100%;
        justify-content: center;
        box-shadow: 0 4px 15px rgba(255, 154, 158, 0.3);
      }

      .btn-primary:hover {
        transform: translateY(-2px);
        box-shadow: 0 6px 20px rgba(255, 154, 158, 0.4);
      }

      .tabs {
        display: flex;
        gap: 10px;
        margin-bottom: 25px;
        border-bottom: 2px solid var(--light-pink);
        padding-bottom: 10px;
      }

      .tab {
        padding: 10px 20px;
        background: transparent;
        border: none;
        color: var(--text-light);
        cursor: pointer;
        font-weight: 600;
        transition: all 0.3s ease;
        position: relative;
      }

      .tab:hover {
        color: var(--primary-rose);
      }

      .tab.active {
        color: var(--primary-rose);
      }

      .tab.active::after {
        content: "";
        position: absolute;
        bottom: -12px;
        left: 0;
        right: 0;
        height: 3px;
        background: var(--primary-rose);
        border-radius: 2px;
        animation: slideIn 0.3s ease;
      }

      .loan-list {
        max-height: 600px;
        overflow-y: auto;
        padding-right: 10px;
      }

      .loan-list::-webkit-scrollbar {
        width: 8px;
      }

      .loan-list::-webkit-scrollbar-track {
        background: var(--light-pink);
        border-radius: 10px;
      }

      .loan-list::-webkit-scrollbar-thumb {
        background: var(--primary-rose);
        border-radius: 10px;
      }

      .loan-item {
        background: var(--light-pink);
        border-radius: 15px;
        padding: 20px;
        margin-bottom: 15px;
        transition: all 0.3s ease;
        animation: slideInRight 0.5s ease;
        position: relative;
      }

      @keyframes slideInRight {
        from {
          opacity: 0;
          transform: translateX(20px);
        }
        to {
          opacity: 1;
          transform: translateX(0);
        }
      }

      .loan-item:hover {
        transform: translateX(-5px);
        box-shadow: 0 5px 20px rgba(255, 154, 158, 0.2);
      }

      .loan-header {
        display: flex;
        justify-content: space-between;
        align-items: flex-start;
        margin-bottom: 15px;
      }

      .borrower-name {
        font-size: 1.2rem;
        font-weight: bold;
        color: var(--text-dark);
      }

      .loan-status {
        padding: 5px 12px;
        border-radius: 20px;
        font-size: 0.85rem;
        font-weight: 600;
        color: white;
      }

      .status-active {
        background: var(--success);
      }

      .status-due {
        background: var(--warning);
      }

      .status-overdue {
        background: var(--danger);
        animation: blink 1.5s infinite;
      }

      @keyframes blink {
        0%,
        100% {
          opacity: 1;
        }
        50% {
          opacity: 0.7;
        }
      }

      .loan-details {
        display: grid;
        grid-template-columns: 1fr 1fr;
        gap: 10px;
        margin-bottom: 15px;
      }

      .detail-item {
        display: flex;
        flex-direction: column;
      }

      .detail-label {
        font-size: 0.85rem;
        color: var(--text-light);
        margin-bottom: 3px;
      }

      .detail-value {
        font-weight: 600;
        color: var(--text-dark);
      }

      .late-fee {
        background: rgba(235, 59, 90, 0.1);
        color: var(--danger);
        padding: 10px;
        border-radius: 10px;
        margin-bottom: 15px;
        display: flex;
        align-items: center;
        gap: 10px;
      }

      .loan-actions {
        display: flex;
        gap: 10px;
      }

      .btn-small {
        padding: 8px 15px;
        font-size: 0.9rem;
        flex: 1;
      }

      .btn-extend {
        background: var(--warning);
        color: white;
      }

      .btn-pay {
        background: var(--success);
        color: white;
      }

      .btn-detail {
        background: var(--primary-rose);
        color: white;
      }

      .empty-state {
        text-align: center;
        padding: 60px 20px;
        color: var(--text-light);
      }

      .empty-state i {
        font-size: 4rem;
        margin-bottom: 20px;
        opacity: 0.5;
        color: var(--primary-rose);
      }

      .modal {
        display: none;
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(0, 0, 0, 0.5);
        z-index: 1000;
        animation: fadeIn 0.3s ease;
      }

      .modal.show {
        display: flex;
        justify-content: center;
        align-items: center;
      }

      .modal-content {
        background: white;
        padding: 30px;
        border-radius: 25px;
        max-width: 500px;
        width: 90%;
        animation: slideUp 0.3s ease;
      }

      .modal-header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        margin-bottom: 20px;
      }

      .modal-close {
        background: transparent;
        border: none;
        font-size: 1.5rem;
        cursor: pointer;
        color: var(--text-light);
        transition: color 0.3s ease;
      }

      .modal-close:hover {
        color: var(--danger);
      }

      .notification {
        position: fixed;
        top: 20px;
        right: 20px;
        background: white;
        padding: 15px 20px;
        border-radius: 12px;
        box-shadow: var(--shadow);
        display: flex;
        align-items: center;
        gap: 10px;
        transform: translateX(400px);
        transition: transform 0.3s ease;
        z-index: 2000;
      }

      .notification.show {
        transform: translateX(0);
      }

      .notification.success {
        border-left: 4px solid var(--success);
      }

      .notification.warning {
        border-left: 4px solid var(--warning);
      }

      .notification.error {
        border-left: 4px solid var(--danger);
      }

      @media (max-width: 1024px) {
        .main-content {
          grid-template-columns: 1fr;
        }
      }

      @media (max-width: 768px) {
        .input-group {
          grid-template-columns: 1fr;
        }

        .loan-details {
          grid-template-columns: 1fr;
        }

        .loan-actions {
          flex-direction: column;
        }

        h1 {
          font-size: 1.8rem;
        }
      }
    </style>
  </head>
  <body>
    <div class="container">
      <header>
        <div class="header-content">
          <div class="logo">
            <i class="fas fa-hand-holding-usd"></i>
            <h1>AmanahKu</h1>
          </div>
          <div class="date-time">
            <div id="currentDate"></div>
            <div id="currentTime"></div>
          </div>
        </div>
      </header>

      <div class="dashboard">
        <div class="stat-card">
          <div class="stat-icon">
            <i class="fas fa-users"></i>
          </div>
          <div class="stat-value" id="activeLoans">0</div>
          <div class="stat-label">Pinjaman Aktif</div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <i class="fas fa-money-bill-wave"></i>
          </div>
          <div class="stat-value" id="totalLent">Rp 0</div>
          <div class="stat-label">Total Dipinjamkan</div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <i class="fas fa-coins"></i>
          </div>
          <div class="stat-value" id="totalEarned">Rp 0</div>
          <div class="stat-label">Total Keuntungan</div>
        </div>

        <div class="stat-card">
          <div class="stat-icon">
            <i class="fas fa-exclamation-triangle"></i>
          </div>
          <div class="stat-value" id="overdueLoans">0</div>
          <div class="stat-label">Pinjaman Telat</div>
        </div>
      </div>

      <div class="main-content">
        <div class="card">
          <h2 class="card-title">
            <i class="fas fa-plus-circle"></i>
            Tambah Pinjaman Baru
          </h2>
          <form id="loanForm">
            <div class="form-group">
              <label for="borrowerName">Nama Peminjam</label>
              <input type="text" id="borrowerName" placeholder="Masukkan nama peminjam..." required />
            </div>

            <div class="input-group">
              <div class="form-group">
                <label for="amount">Jumlah Pinjaman (Rp)</label>
                <input type="number" id="amount" placeholder="0" required min="10000" step="10000" />
              </div>

              <div class="form-group">
                <label for="interest">Bunga (%)</label>
                <input type="number" id="interest" placeholder="10" required min="0" max="100" step="1" />
              </div>
            </div>

            <div class="input-group">
              <div class="form-group">
                <label for="duration">Durasi (Hari)</label>
                <input type="number" id="duration" placeholder="7" required min="1" value="7" />
              </div>

              <div class="form-group">
                <label for="dueDate">Jatuh Tempo</label>
                <input type="date" id="dueDate" required />
              </div>
            </div>

            <div class="form-group">
              <label for="notes">Catatan (Opsional)</label>
              <textarea id="notes" rows="3" placeholder="Tambahkan catatan..."></textarea>
            </div>

            <button type="submit" class="btn btn-primary">
              <i class="fas fa-save"></i>
              Tambah Pinjaman
            </button>
          </form>
        </div>

        <div class="card">
          <h2 class="card-title">
            <i class="fas fa-list"></i>
            Daftar Pinjaman
          </h2>

          <div class="tabs">
            <button class="tab active" data-tab="active">Aktif</button>
            <button class="tab" data-tab="due">Jatuh Tempo</button>
            <button class="tab" data-tab="overdue">Telat</button>
            <button class="tab" data-tab="paid">Lunas</button>
          </div>

          <div class="loan-list" id="loanList">
            <div class="empty-state">
              <i class="fas fa-clipboard-list"></i>
              <p>Belum ada data pinjaman</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="modal" id="extendModal">
      <div class="modal-content">
        <div class="modal-header">
          <h3>Perpanjang Jatuh Tempo</h3>
          <button class="modal-close" onclick="closeModal()">
            <i class="fas fa-times"></i>
          </button>
        </div>
        <form id="extendForm">
          <div class="form-group">
            <label for="newDueDate">Tanggal Jatuh Tempo Baru</label>
            <input type="date" id="newDueDate" required />
          </div>
          <div class="form-group">
            <label for="extendReason">Alasan Perpanjangan</label>
            <textarea id="extendReason" rows="3" placeholder="Masukkan alasan perpanjangan..."></textarea>
          </div>
          <button type="submit" class="btn btn-primary">
            <i class="fas fa-calendar-check"></i>
            Perpanjang
          </button>
        </form>
      </div>
    </div>

    <div class="notification" id="notification">
      <i class="fas fa-check-circle"></i>
      <span id="notificationText">Notifikasi</span>
    </div>

    <script>
      class LoanManager {
        constructor() {
          this.loans = JSON.parse(localStorage.getItem("loans")) || [];
          this.currentTab = "active";
          this.extendingLoanId = null;
          this.init();
        }

        init() {
          this.setupEventListeners();
          this.updateDateTime();
          this.setDefaultDueDate();
          this.renderLoans();
          this.updateStats();

          // Update time every second
          setInterval(() => this.updateDateTime(), 1000);

          // Check due dates every hour
          setInterval(() => this.checkDueDates(), 3600000);
        }

        setupEventListeners() {
          // Loan form
          document.getElementById("loanForm").addEventListener("submit", (e) => {
            e.preventDefault();
            this.addLoan();
          });

          // Extend form
          document.getElementById("extendForm").addEventListener("submit", (e) => {
            e.preventDefault();
            this.extendDueDate();
          });

          // Duration change
          document.getElementById("duration").addEventListener("change", (e) => {
            this.updateDueDate(e.target.value);
          });

          // Tabs
          document.querySelectorAll(".tab").forEach((tab) => {
            tab.addEventListener("click", (e) => {
              document.querySelectorAll(".tab").forEach((t) => t.classList.remove("active"));
              e.target.classList.add("active");
              this.currentTab = e.target.dataset.tab;
              this.renderLoans();
            });
          });
        }

        updateDateTime() {
          const now = new Date();
          const dateOptions = { weekday: "long", year: "numeric", month: "long", day: "numeric" };
          const timeOptions = { hour: "2-digit", minute: "2-digit", second: "2-digit" };

          document.getElementById("currentDate").textContent = now.toLocaleDateString("id-ID", dateOptions);
          document.getElementById("currentTime").textContent = now.toLocaleTimeString("id-ID", timeOptions);
        }

        setDefaultDueDate() {
          const duration = document.getElementById("duration").value || 7;
          this.updateDueDate(duration);
        }

        updateDueDate(days) {
          const dueDate = new Date();
          dueDate.setDate(dueDate.getDate() + parseInt(days));
          document.getElementById("dueDate").value = dueDate.toISOString().split("T")[0];
        }

        addLoan() {
          const borrowerName = document.getElementById("borrowerName").value;
          const amount = parseFloat(document.getElementById("amount").value);
          const interest = parseFloat(document.getElementById("interest").value);
          const duration = parseInt(document.getElementById("duration").value);
          const dueDate = document.getElementById("dueDate").value;
          const notes = document.getElementById("notes").value;

          const totalInterest = (amount * interest) / 100;
          const totalRepayment = amount + totalInterest;

          const loan = {
            id: Date.now(),
            borrowerName,
            amount,
            interest,
            totalInterest,
            totalRepayment,
            duration,
            dueDate,
            originalDueDate: dueDate,
            notes,
            status: "active",
            createdAt: new Date().toISOString(),
            extensions: [],
          };

          this.loans.push(loan);
          this.saveLoans();
          this.renderLoans();
          this.updateStats();
          this.showNotification("Pinjaman berhasil ditambahkan!", "success");

          // Reset form
          document.getElementById("loanForm").reset();
          this.setDefaultDueDate();
        }

        renderLoans() {
          const loanList = document.getElementById("loanList");
          let filteredLoans = this.getFilteredLoans();

          if (filteredLoans.length === 0) {
            loanList.innerHTML = `
                        <div class="empty-state">
                            <i class="fas fa-clipboard-list"></i>
                            <p>Tidak ada pinjaman ${this.getTabLabel()}</p>
                        </div>
                    `;
            return;
          }

          loanList.innerHTML = filteredLoans.map((loan) => this.createLoanHTML(loan)).join("");
        }

        getFilteredLoans() {
          const today = new Date();
          today.setHours(0, 0, 0, 0);

          return this.loans.filter((loan) => {
            const dueDate = new Date(loan.dueDate);
            dueDate.setHours(0, 0, 0, 0);
            const daysDiff = Math.ceil((dueDate - today) / (1000 * 60 * 60 * 24));

            switch (this.currentTab) {
              case "active":
                return loan.status === "active" && daysDiff > 0;
              case "due":
                return loan.status === "active" && daysDiff === 0;
              case "overdue":
                return loan.status === "active" && daysDiff < 0;
              case "paid":
                return loan.status === "paid";
              default:
                return false;
            }
          });
        }

        createLoanHTML(loan) {
          const today = new Date();
          today.setHours(0, 0, 0, 0);
          const dueDate = new Date(loan.dueDate);
          dueDate.setHours(0, 0, 0, 0);
          const daysDiff = Math.ceil((dueDate - today) / (1000 * 60 * 60 * 24));

          let status = "status-active";
          let statusText = "Aktif";

          if (daysDiff === 0) {
            status = "status-due";
            statusText = "Jatuh Tempo Hari Ini";
          } else if (daysDiff < 0) {
            status = "status-overdue";
            statusText = `Telat ${Math.abs(daysDiff)} Hari`;
          }

          const lateFee = daysDiff < 0 ? Math.abs(daysDiff) * 10000 : 0;
          const totalWithLateFee = loan.totalRepayment + lateFee;

          return `
                    <div class="loan-item">
                        <div class="loan-header">
                            <div class="borrower-name">${loan.borrowerName}</div>
                            <div class="loan-status ${status}">${statusText}</div>
                        </div>
                        
                        <div class="loan-details">
                            <div class="detail-item">
                                <span class="detail-label">Pinjaman</span>
                                <span class="detail-value">Rp ${this.formatNumber(loan.amount)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Bunga</span>
                                <span class="detail-value">${loan.interest}% (Rp ${this.formatNumber(loan.totalInterest)})</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Total Tagihan</span>
                                <span class="detail-value">Rp ${this.formatNumber(loan.totalRepayment)}</span>
                            </div>
                            <div class="detail-item">
                                <span class="detail-label">Jatuh Tempo</span>
                                <span class="detail-value">${this.formatDate(loan.dueDate)}</span>
                            </div>
                        </div>

                        ${
                          lateFee > 0
                            ? `
                            <div class="late-fee">
                                <i class="fas fa-exclamation-circle"></i>
                                <div>
                                    <strong>Denda Keterlambatan:</strong> Rp ${this.formatNumber(lateFee)} 
                                    (${Math.abs(daysDiff)} hari × Rp 10.000)
                                </div>
                            </div>
                        `
                            : ""
                        }

                        ${
                          lateFee > 0
                            ? `
                            <div class="loan-details" style="margin-bottom: 15px;">
                                <div class="detail-item">
                                    <span class="detail-label">Total Pembayaran</span>
                                    <span class="detail-value" style="color: var(--danger); font-size: 1.1rem;">
                                        Rp ${this.formatNumber(totalWithLateFee)}
                                    </span>
                                </div>
                            </div>
                        `
                            : ""
                        }

                        <div class="loan-actions">
                            ${
                              loan.status === "active"
                                ? `
                                <button class="btn btn-small btn-extend" onclick="loanManager.openExtendModal(${loan.id})">
                                    <i class="fas fa-calendar-plus"></i> Perpanjang
                                </button>
                                <button class="btn btn-small btn-pay" onclick="loanManager.markAsPaid(${loan.id})">
                                    <i class="fas fa-check"></i> Lunasi
                                </button>
                            `
                                : ""
                            }
                            <button class="btn btn-small btn-detail" onclick="loanManager.showDetail(${loan.id})">
                                <i class="fas fa-info-circle"></i> Detail
                            </button>
                        </div>
                    </div>
                `;
        }

        openExtendModal(loanId) {
          this.extendingLoanId = loanId;
          const loan = this.loans.find((l) => l.id === loanId);
          if (loan) {
            document.getElementById("newDueDate").value = loan.dueDate;
            document.getElementById("extendModal").classList.add("show");
          }
        }

        extendDueDate() {
          const loan = this.loans.find((l) => l.id === this.extendingLoanId);
          if (!loan) return;

          const newDueDate = document.getElementById("newDueDate").value;
          const reason = document.getElementById("extendReason").value;

          // Add to extension history
          loan.extensions.push({
            oldDate: loan.dueDate,
            newDate: newDueDate,
            reason: reason,
            extendedAt: new Date().toISOString(),
          });

          loan.dueDate = newDueDate;
          this.saveLoans();
          this.renderLoans();
          this.updateStats();
          this.closeModal();
          this.showNotification("Jatuh tempo berhasil diperpanjang!", "success");
        }

        markAsPaid(loanId) {
          const loan = this.loans.find((l) => l.id === loanId);
          if (!loan) return;

          if (confirm(`Apakah Anda yakin pinjaman ${loan.borrowerName} sudah lunas?`)) {
            loan.status = "paid";
            loan.paidDate = new Date().toISOString();

            // Calculate total earned
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const dueDate = new Date(loan.dueDate);
            dueDate.setHours(0, 0, 0, 0);
            const daysDiff = Math.ceil((dueDate - today) / (1000 * 60 * 60 * 24));
            const lateFee = daysDiff < 0 ? Math.abs(daysDiff) * 10000 : 0;
            loan.totalEarned = loan.totalInterest + lateFee;

            this.saveLoans();
            this.renderLoans();
            this.updateStats();
            this.showNotification("Pinjaman telah dilunasi!", "success");
          }
        }

        showDetail(loanId) {
          const loan = this.loans.find((l) => l.id === loanId);
          if (!loan) return;

          let extensionsInfo = "";
          if (loan.extensions.length > 0) {
            extensionsInfo = loan.extensions.map((ext) => `Diperpanjang dari ${this.formatDate(ext.oldDate)} ke ${this.formatDate(ext.newDate)}`).join("\n");
          }

          alert(`
                    Detail Pinjaman:
                    Nama: ${loan.borrowerName}
                    Jumlah: Rp ${this.formatNumber(loan.amount)}
                    Bunga: ${loan.interest}%
                    Total: Rp ${this.formatNumber(loan.totalRepayment)}
                    Jatuh Tempo: ${this.formatDate(loan.dueDate)}
                    Status: ${loan.status === "paid" ? "Lunas" : "Aktif"}
                    Catatan: ${loan.notes || "-"}
                    ${extensionsInfo ? "\nRiwayat Perpanjangan:\n" + extensionsInfo : ""}
                `);
        }

        updateStats() {
          const activeLoans = this.loans.filter((l) => l.status === "active");
          const overdueLoans = activeLoans.filter((l) => {
            const today = new Date();
            today.setHours(0, 0, 0, 0);
            const dueDate = new Date(l.dueDate);
            dueDate.setHours(0, 0, 0, 0);
            return dueDate < today;
          });

          const totalLent = this.loans.reduce((sum, l) => sum + l.amount, 0);
          const totalEarned = this.loans.reduce((sum, l) => sum + (l.totalEarned || l.totalInterest || 0), 0);

          document.getElementById("activeLoans").textContent = activeLoans.length;
          document.getElementById("totalLent").textContent = `Rp ${this.formatNumber(totalLent)}`;
          document.getElementById("totalEarned").textContent = `Rp ${this.formatNumber(totalEarned)}`;
          document.getElementById("overdueLoans").textContent = overdueLoans.length;
        }

        checkDueDates() {
          const today = new Date();
          today.setHours(0, 0, 0, 0);

          this.loans.forEach((loan) => {
            if (loan.status !== "active") return;

            const dueDate = new Date(loan.dueDate);
            dueDate.setHours(0, 0, 0, 0);
            const daysDiff = Math.ceil((dueDate - today) / (1000 * 60 * 60 * 24));

            if (daysDiff === 1) {
              this.showNotification(`Pinjaman ${loan.borrowerName} jatuh tempo besok!`, "warning");
            } else if (daysDiff === 0) {
              this.showNotification(`Pinjaman ${loan.borrowerName} jatuh tempo hari ini!`, "warning");
            } else if (daysDiff < 0 && Math.abs(daysDiff) % 3 === 0) {
              const lateFee = Math.abs(daysDiff) * 10000;
              this.showNotification(`Pinjaman ${loan.borrowerName} telat ${Math.abs(daysDiff)} hari (Denda: Rp ${this.formatNumber(lateFee)})`, "error");
            }
          });
        }

        getTabLabel() {
          const labels = {
            active: "aktif",
            due: "yang jatuh tempo",
            overdue: "yang telat",
            paid: "yang telah lunas",
          };
          return labels[this.currentTab] || "";
        }

        formatNumber(num) {
          return new Intl.NumberFormat("id-ID").format(num);
        }

        formatDate(dateString) {
          const options = { day: "numeric", month: "long", year: "numeric" };
          return new Date(dateString).toLocaleDateString("id-ID", options);
        }

        showNotification(message, type = "success") {
          const notification = document.getElementById("notification");
          const notificationText = document.getElementById("notificationText");

          notification.className = `notification ${type}`;
          notificationText.textContent = message;

          const icon = notification.querySelector("i");
          icon.className = type === "success" ? "fas fa-check-circle" : type === "warning" ? "fas fa-exclamation-circle" : "fas fa-times-circle";

          notification.classList.add("show");

          setTimeout(() => {
            notification.classList.remove("show");
          }, 4000);
        }

        saveLoans() {
          localStorage.setItem("loans", JSON.stringify(this.loans));
        }
      }

      // Global functions
      function closeModal() {
        document.getElementById("extendModal").classList.remove("show");
        document.getElementById("extendForm").reset();
      }

      // Initialize the app
      const loanManager = new LoanManager();
    </script>
  </body>
</html>
