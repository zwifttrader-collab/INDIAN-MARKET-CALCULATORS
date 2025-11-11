<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>NIFTY | STOCK | STOCK FUTURES - Position Size Calculators</title>
<style>
  :root{
    --page-bg:#f5faff;
    --card-bg:#fff;
    --accent-yellow:#ffff00;
    --accent-green:#e6f4ea;
    --accent-blue:#dbe9ff;
    --border:#ddd;
    --shadow: 0 6px 18px rgba(0,0,0,0.08);
    --max-width:820px;
  }
  body{
    font-family: Arial, Helvetica, sans-serif;
    background:var(--page-bg);
    margin:20px;
    display:flex;
    justify-content:center;
  }
  .wrap{
    width:100%;
    max-width:var(--max-width);
  }
  header{
    text-align:center;
    background:var(--accent-yellow);
    padding:10px;
    border:2px solid #000;
    font-weight:700;
    color:#000;
  }

  /* Tabs */
  .tabs{
    display:flex;
    gap:8px;
    justify-content:center;
    margin:14px 0;
  }
  .tab-btn{
    padding:8px 14px;
    border-radius:8px;
    border:1px solid var(--border);
    background:#fff;
    cursor:pointer;
    font-weight:600;
  }
  .tab-btn.active{
    background:linear-gradient(180deg,#f0fdfa,#e6f4ea);
    box-shadow:var(--shadow);
  }

  /* Card */
  .card{
    background:var(--card-bg);
    padding:14px;
    border-radius:6px;
    box-shadow:var(--shadow);
    margin-bottom:18px;
  }

  table.calc {
    width:100%;
    border-collapse:collapse;
    margin:8px 0 2px 0;
    table-layout:fixed;
  }
  table.calc td{
    border:1px solid var(--border);
    padding:10px;
    vertical-align:middle;
  }
  table.calc td.label{
    width:65%;
    font-weight:600;
  }
  input[type="number"]{
    width:100%;
    box-sizing:border-box;
    padding:6px 8px;
    border-radius:4px;
    border:1px solid #cfcfcf;
    text-align:right;
    font-size:14px;
  }

  /* Highlight rows */
  .highlight{
    background:var(--accent-green);
    font-weight:700;
  }
  .note{
    background:var(--accent-blue);
    padding:10px;
    text-align:center;
    margin-top:10px;
    border-radius:4px;
    font-size:14px;
  }

  /* small responsive */
  @media (max-width:640px){
    table.calc td.label{width:55%;}
    .tabs{flex-wrap:wrap;}
  }
</style>
</head>
<body>
  <div class="wrap">
    <header><h1 style="margin:0;font-size:18px">POSITION SIZE CALCULATORS</h1></header>

    <div class="tabs" role="tablist" aria-label="Calculators">
      <button class="tab-btn active" data-tab="nifty">NIFTY 50 (Selling)</button>
      <button class="tab-btn" data-tab="stock">STOCK</button>
      <button class="tab-btn" data-tab="futures">STOCK FUTURES</button>
    </div>

    <!-- NIFTY -->
    <div id="nifty" class="card tab-panel">
      <h3 style="text-align:center;margin:6px 0;background:var(--accent-yellow);padding:6px;border-radius:6px;border:1px solid #000;">NIFTY 50 POSITION SIZE CALCULATOR (FOR SELLING)</h3>
      <table class="calc">
        <tr><td class="label">Account Balance (₹)</td><td><input id="n_acc" type="number" value="1000000" /></td></tr>
        <tr><td class="label">Risk % per trade</td><td><input id="n_riskPct" type="number" value="1" step="0.01" /></td></tr>
        <tr><td class="label">Risk Per Trade (₹)</td><td><input id="n_riskAmt" type="number" value="10000" /></td></tr>
        <tr><td class="label">Entry Price</td><td><input id="n_entry" type="number" value="110" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Price</td><td><input id="n_sl" type="number" value="140" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Point</td><td><input id="n_slPoint" type="number" value="30" step="0.01" /></td></tr>
        <tr><td class="label">Nifty Lot Size</td><td><input id="n_lot" type="number" value="75" /></td></tr>

        <tr class="highlight"><td>Total Loss Calculated (₹)</td><td id="n_total">2250</td></tr>
        <tr class="highlight"><td>Position Size</td><td id="n_pos">4.4444</td></tr>
      </table>
      <div class="note">• Change any input (Account Balance, Risk %, Entry, Stop Loss, Lot Size) and calculated fields update automatically.</div>
    </div>

    <!-- STOCK -->
    <div id="stock" class="card tab-panel" style="display:none">
      <h3 style="text-align:center;margin:6px 0;background:var(--accent-yellow);padding:6px;border-radius:6px;border:1px solid #000;">STOCK POSITION SIZE CALCULATOR</h3>
      <table class="calc">
        <tr><td class="label">Account Balance (₹)</td><td><input id="s_acc" type="number" value="100000" /></td></tr>
        <tr><td class="label">Risk % per trade</td><td><input id="s_riskPct" type="number" value="1" step="0.01" /></td></tr>
        <tr><td class="label">Risk Per Trade (₹)</td><td><input id="s_riskAmt" type="number" value="1000" /></td></tr>
        <tr><td class="label">Entry Price</td><td><input id="s_entry" type="number" value="119" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Price</td><td><input id="s_sl" type="number" value="115" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Point</td><td><input id="s_slPoint" type="number" value="4" step="0.01" /></td></tr>

        <tr class="highlight"><td>Position Size (shares)</td><td id="s_pos">250</td></tr>
      </table>
      <div class="note">• Stock position = Risk amount ÷ Stop-loss points (round or trim as needed).</div>
    </div>

    <!-- FUTURES -->
    <div id="futures" class="card tab-panel" style="display:none">
      <h3 style="text-align:center;margin:6px 0;background:var(--accent-yellow);padding:6px;border-radius:6px;border:1px solid #000;">STOCK FUTURES CALCULATOR</h3>
      <table class="calc">
        <tr><td class="label">Account Balance (₹)</td><td><input id="f_acc" type="number" value="1000000" /></td></tr>
        <tr><td class="label">Risk % per trade</td><td><input id="f_riskPct" type="number" value="1" step="0.01" /></td></tr>
        <tr><td class="label">Risk Per Trade (₹)</td><td><input id="f_riskAmt" type="number" value="10000" /></td></tr>
        <tr><td class="label">Entry Price</td><td><input id="f_entry" type="number" value="958.7" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Price</td><td><input id="f_sl" type="number" value="960.6" step="0.01" /></td></tr>
        <tr><td class="label">Stop Loss Point</td><td><input id="f_slPoint" type="number" value="1.9" step="0.01" /></td></tr>
        <tr><td class="label">Stock Lot Size</td><td><input id="f_lot" type="number" value="750" /></td></tr>

        <tr class="highlight"><td>Total Loss Calculated (₹)</td><td id="f_total">1425</td></tr>
        <tr class="highlight"><td>Position Size</td><td id="f_pos">7.01754386</td></tr>
      </table>
      <div class="note">• Change any input (Account Balance, Risk %, Entry, Stop Loss, Lot Size) and calculated fields update automatically.</div>
    </div>

  </div>

<script>
  // Tab switching
  document.querySelectorAll('.tab-btn').forEach(btn=>{
    btn.addEventListener('click',()=>{
      document.querySelectorAll('.tab-btn').forEach(b=>b.classList.remove('active'));
      btn.classList.add('active');
      const target = btn.getAttribute('data-tab');
      document.querySelectorAll('.tab-panel').forEach(p=>{
        p.style.display = (p.id === target) ? 'block' : 'none';
      });
    });
  });

  // Calculations with safe guards (no divide by 0)
  function calcNifty(){
    const acc = parseFloat(document.getElementById('n_acc').value) || 0;
    const pct = parseFloat(document.getElementById('n_riskPct').value) || 0;
    const entry = parseFloat(document.getElementById('n_entry').value) || 0;
    const sl = parseFloat(document.getElementById('n_sl').value) || 0;
    const lot = parseFloat(document.getElementById('n_lot').value) || 0;

    const riskAmt = acc * (pct/100);
    document.getElementById('n_riskAmt').value = riskAmt.toFixed(2);

    const slPoint = Math.abs(sl - entry);
    document.getElementById('n_slPoint').value = slPoint.toFixed(2);

    const total = slPoint * lot;
    document.getElementById('n_total').textContent = (isFinite(total)? total.toFixed(2) : '0.00');

    const pos = (total > 0) ? (riskAmt / total) : 0;
    document.getElementById('n_pos').textContent = isFinite(pos)? pos.toFixed(4) : '0.0000';
  }

  function calcStock(){
    const acc = parseFloat(document.getElementById('s_acc').value) || 0;
    const pct = parseFloat(document.getElementById('s_riskPct').value) || 0;
    const entry = parseFloat(document.getElementById('s_entry').value) || 0;
    const sl = parseFloat(document.getElementById('s_sl').value) || 0;

    const riskAmt = acc * (pct/100);
    document.getElementById('s_riskAmt').value = riskAmt.toFixed(2);

    const slPoint = Math.abs(entry - sl);
    document.getElementById('s_slPoint').value = slPoint.toFixed(2);

    const pos = (slPoint > 0) ? (riskAmt / slPoint) : 0;
    // show whole shares if it's whole, else show 2 decimals
    const posText = (Math.abs(pos - Math.round(pos)) < 1e-9) ? String(Math.round(pos)) : pos.toFixed(2);
    document.getElementById('s_pos').textContent = isFinite(pos)? posText : '0';
  }

  function calcFutures(){
    const acc = parseFloat(document.getElementById('f_acc').value) || 0;
    const pct = parseFloat(document.getElementById('f_riskPct').value) || 0;
    const entry = parseFloat(document.getElementById('f_entry').value) || 0;
    const sl = parseFloat(document.getElementById('f_sl').value) || 0;
    const lot = parseFloat(document.getElementById('f_lot').value) || 0;

    const riskAmt = acc * (pct/100);
    document.getElementById('f_riskAmt').value = riskAmt.toFixed(2);

    const slPoint = Math.abs(sl - entry);
    document.getElementById('f_slPoint').value = slPoint.toFixed(2);

    const total = slPoint * lot;
    document.getElementById('f_total').textContent = isFinite(total)? total.toFixed(2) : '0.00';

    const pos = (total > 0) ? (riskAmt / total) : 0;
    document.getElementById('f_pos').textContent = isFinite(pos)? pos.toFixed(8) : '0.00000000';
  }

  // wire inputs
  document.querySelectorAll('input[type=number]').forEach(inp=>{
    inp.addEventListener('input', ()=>{
      calcNifty();
      calcStock();
      calcFutures();
    });
  });

  // initial calc
  calcNifty(); calcStock(); calcFutures();
</script>
</body>
</html>
